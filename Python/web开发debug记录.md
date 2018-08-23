    Traceback (most recent call last):
    File "/Users/mac/Desktop/python/finder/venv/lib/python3.6/site-packages/web/application.py", line 257, in process
      return self.handle()
    File "/Users/mac/Desktop/python/finder/venv/lib/python3.6/site-packages/web/application.py", line 248, in handle
      return self._delegate(fn, self.fvars, args)
    File "/Users/mac/Desktop/python/finder/venv/lib/python3.6/site-packages/web/application.py", line 488, in _delegate
      return handle_class(cls)
    File "/Users/mac/Desktop/python/finder/venv/lib/python3.6/site-packages/web/application.py", line 466, in handle_class
      return tocall(*args)
    File "/Users/mac/Desktop/python/finder/venv/finder.py", line 19, in GET
      res = model.get_file(pid)
    File "/Users/mac/Desktop/python/finder/venv/model.py", line 51, in get_file
      raise e
    File "/Users/mac/Desktop/python/finder/venv/model.py", line 33, in get_file
      cursor.execute('select id,type,file_name,obj_name, size, parent, child, createTime, lastModifedTime, saveTime, sharedId, MD5 from files where parent = ?', pid)
    sqlite3.ProgrammingError: SQLite objects created in a thread can only be used in that same thread.The object was created in thread id 140736089248704 and this is thread id 123145389125632


sqlite本身应对多个线程并发访问过程中的冲突问题，由一个线程创建并访问的sqlite的数据库，无法允许另外一个线程进行访问。这里的解决办法可能有２个：

　通过队列规避多线程的访问
　通过设置或者多个访问管道，规避线程之间的冲突问题

#### 利用sqlite3.connect(file_path, check_same_thread=False) 参数设置允许多线程访问，可能会不安全
  