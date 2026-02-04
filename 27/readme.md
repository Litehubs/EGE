ВСЕ ТИПЫ 27 ЗАДАЧ

напоминалка: Aбсолютное значение целой части = print(Px //1, Py//1)

АЛГОРИТМ ДБ СКАН:


                                    import math
                                    f = open('27B.txt')
                                    f.readline()
                                    points = [list(map(float, s.replace(',','.').split())) for s in f]
                                    clusters, epsilon = [], 0.5
                                    while points:
                                        clusters.append([points[0]])
                                        del points[0]
                                        for p1 in clusters[-1]:
                                            for p2 in points[:]:
                                                if math.dist(p1,p2) < epsilon:
                                                    clusters[-1].append(p2)
                                                    points.remove(p2)
                                    best_centroids = [[] for _ in range(len(clusters))]
                                    for i in range(len(clusters)):
                                        min_sum_dist = 10**10
                                        for x1, y1 in clusters[i]:
                                            sum_dist = 0
                                            for x2, y2 in clusters[i]:
                                                sum_dist += math.dist([x1,y1], [x2,y2])
                                            if sum_dist < min_sum_dist:
                                                min_sum_dist = sum_dist
                                                best_centroids[i] = [x1,y1]
                                    Px = (sum([x for x,y in best_centroids])/len(clusters)) * 10000
                                    Py = (sum([y for x,y in best_centroids])/len(clusters)) * 10000
                                    print(int(Px), int(Py))
