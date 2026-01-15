Базовый код Вики:


            def g(x,s,p,end):
                if (x + s) >= 73: return p in end
                if (x + s) < 73 and p == max(end): return False
                moves = [g(x,s+ 2,p + 1, end),g(x,s + 2,p + 1, end),
                         g(x,s * 2,p + 1, end), g(x,s *  2,p + 1, end)]
                return any(moves) if (p + 1) % 2 == (end[0] % 2 ) else all(moves)
            x = 4
            print([s for s in range(1,69) if g(x, s,0,[1])])




КОД Кабанова:        


            def f(a,b,m):
    if (a + b) >= 59: return m % 2 == 0
    if m == 0: return 0
    h = [f(a + 1,b, m-1),f(a * 2,b, m-1),
         f(a, b +1 , m-1), f(a,b * 2, m-1)]
    return any(h) if (m - 1) % 2 ==0 else all(h)
     print([s for s in range(1,54) if f(8,s,3) and not f(8,s,1)])
     print([s for s in range(1,54) if f(8,s,4) and not f(8,s,2)])
     #19 - 1325
     # 20 - 2124
     # 21 -  20
