Задачи 23 (уровень изи) и +хард

моя идейка (лайфхак): 

  def task(start,end):   
  
    if start > end:
      
        return 0

    if start == end:
  
        return 1
    return task(start + 2,end) + task(start * 2, end)
    
  print(task(3,15) * task(15,72) - task(27, 72)) 
