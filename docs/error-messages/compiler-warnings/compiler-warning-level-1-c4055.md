---
---
# <a name="compiler-warning-level-1-c4055"></a>Kompilator C4055 ostrzegawcze (poziom 1)  
  
"konwersji": ze wskaźnika danych "type1" do wskaźnika funkcji "type2".  
  
**Wygasłe:** to ostrzeżenie nie jest generowany przez Visual Studio 2017 i nowszych wersjach.

 Wskaźnik danych jest rzutowane (prawdopodobnie nieprawidłowo) na wskaźnik funkcji. Jest to ostrzeżenia poziomu 1, w obszarze /Za i ostrzeżenie poziom 4 w obszarze /Ze.  
  
 Poniższy przykład generuje C4055:  
  
```C  
// C4055.c  
// compile with: /Za /W1 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
   return (PFUNC)pi;   // C4055  
}  
```  
  
 W obszarze /Ze to ostrzeżenie poziom 4.  
  
```C  
// C4055b.c  
// compile with: /W4 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
return (PFUNC)pi;   // C4055  
}  
```