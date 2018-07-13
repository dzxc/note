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
  
  