# NOOB
l={}
from itertools import combinations
main_set={'a','e','i','o','u'}
for i in "aeiou":
	l[i]=[[],0]
comb=list(combinations(['a','e','i','o','u'],2))
com=list(combinations(['a','e','i','o','u'],3))
co=list(combinations(['a','e','i','o','u'],4))
for i in list(comb):
	i=list(i)
	i.sort()
	l["".join(i)]=[[],0]
for i in com:
	i=list(i)
	i.sort()
	l["".join(i)]=[[],0]
for i in co:
	i=list(i)
	i.sort()
	l["".join(i)]=[[],0]
l['aeiou']=[[],0]
#print(l)
g=sorted(l)

#print(g)
for i in range(len(g)):
	temp_set=list(main_set-set(g[i]))
	temp_set.sort()
	#print(g[i],temp_set,end=' ')
	for j in range(i+1,len(g)):
		#print(g[j],end=' ')
		for k in temp_set:
			if k not in g[j]:
				break
		else:
			l[g[i]][0].append(g[j])
			#print("gya")
	#print("\n\n")
#print(g)	
#print(l)	
#for i in l.keys():
	#print(i,l[i])
from itertools import permutations
cc=list(permutations("aeiou"))
#print(l)
#print(cc)
t=int(input())
for _ in range(t):
	n=int(input())
	a=[]
	for _ in range(n):
		gray=set(input())
		gray=list(gray)
		gray.sort()
		gray="".join(gray)
		l[gray][1]+=1
		#print(gray)
	gg=0
	for i in g:
		if l[i][1]>0:
			#print(i)
			#print()
			for j in l[i][0]:
				#print(i,j,end=' ')
				gg+=l[j][1]*l[i][1]
				#print(gg)
	if l['aeiou'][1]>1:
		lala=l['aeiou'][1]
		gg+=(lala*(lala-1))//2
	for i in g:
		l[i][1]=0
	print(gg)
