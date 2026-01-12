Задачи 23 (уровень изи) и +хард


    def task(start,end):   
    if start > end:
        return 0
    if start == end:
        return 1
    return task(start + 2,end) + task(start * 2, end)  
