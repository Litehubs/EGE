ВСЕ ТИПЫ 27 ЗАДАЧ

напоминалка: Aбсолютное значение целой части = print(Px //1, Py//1)

АЛГОРИТМ ДБ СКАН:

                                                from math import *
                                          from turtle import *
                                          def visual(clusters):
                                              k =50
                                              tracer(0), screensize(3000,3000),penup()
                                              colors = ('green','blue','pink','black')
                                              for i in range(len(clusters)):
                                                  for x,y in clusters[i]:
                                                      setpos(x*k, y * k)
                                                      dot(10,colors[i])
                                              done()
                                          
                                          f = open('27_3.txt')
                                          f.readline()
                                          points = [list(map(float, s.replace(',','.').split())) for s in f]
                                          clusters, epsilon = [], 1
                                          while points:
                                              clusters.append([points[0]])
                                              del  points[0]
                                              for p1 in clusters[-1]:
                                                  for p2 in points[:]:
                                                      if dist(p1,p2) < epsilon:
                                                          clusters[-1].append(p2)
                                                          points.remove(p2)
                                              if len(clusters[-1]) <= 3:
                                                  del clusters[-1]
                                          visual(clusters)
                                          print(len(clusters))
                                          best_centroids = [[] for _ in range(len(clusters))]
                                          for i in range(len(clusters)):
                                              min_sum_dist = 10**10
                                              for x1, y1 in clusters[i]:
                                                  sum_dist = 0
                                                  for x2, y2 in clusters[i]:
                                                      sum_dist += dist([x1,y1], [x2,y2])
                                                  if sum_dist < min_sum_dist:
                                                      min_sum_dist = sum_dist
                                                      best_centroids[i] = [x1,y1]
                                          Px = min([x for x, y in best_centroids])
                                          Py = min([y for x, y in best_centroids])
                                          Ps = min([len(cluster)/16 for  cluster in clusters]) * 1000
                                          print(abs((Px* 10000)//1), abs((Py * 10000)//1))
