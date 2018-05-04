---
title: Wskaźniki stałe i nietrwałe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4e76348a4559d68c0c7dacd91d21c39c5b0d8a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="const-and-volatile-pointers"></a>Wskaźniki stałe i nietrwałe
[Const](../cpp/const-cpp.md) i [volatile](../cpp/volatile-cpp.md) zmiany słów kluczowych jak są traktowane wskaźniki. **Const** — słowo kluczowe Określa, czy wskaźnik nie można zmodyfikować po zainicjowaniu; wskaźnika jest chronione przed modyfikacją później.  
  
 Słowo kluczowe `volatile` określa, że wartość skojarzona z nazwą, która po nim następuje, może być modyfikowana przez akcje inne niż te w aplikacji użytkownika. W związku z tym słowo kluczowe `volatile` jest przydatne do deklarowania obiektów w pamięci współdzielonej, do której może uzyskiwać dostęp wiele procesów lub globalnych obszarów danych dla komunikacji z procedurami usług przerwania.  
  
 Kiedy nazwa jest zadeklarowana jako `volatile`, kompilator ładuje ponownie wartość z pamięci po każdym uzyskaniu dostępu do niej przez program. Zmniejsza to znacznie możliwości optymalizacji. Jednakże, gdy stan obiektu może ulegać nieoczekiwanym zmianom, jest to jedyny sposób zapewnienia przewidywalnej wydajności programu.  
  
 Aby zadeklarować obiektu wskazywana przez wskaźnik jako **const** lub `volatile`, użyj deklaracji w postaci:  
  
```  
const char *cpch;  
volatile char *vpch;  
```  
  
 Aby zadeklarować wartość wskaźnika — oznacza to, rzeczywisty adres przechowywanych we wskaźniku — jako **const** lub `volatile`, użyj deklaracji w postaci:  
  
```  
char * const pchc;  
char * volatile pchv;  
```  
  
 Język C++ uniemożliwia przydziałów, które umożliwiałyby modyfikacji obiektu lub wskaźnik zadeklarowane jako **const**. Takie przypisania powodowałyby usunięcie informacji, z którą obiekt lub wskaźnik został zadeklarowany, naruszając w ten sposób zamiar pierwotnej deklaracji. Rozważ następujące deklaracje:  
  
```  
const char cch = 'A';  
char ch = 'B';  
```  
  
 Podane poprzedniej deklaracji dwa obiekty (`cch`, typu **const char**, i `ch`, typu **char)**, deklaracji/inicjalizacji są prawidłowe:  
  
```  
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 Poniższa deklaracja/inicjacje są błędne.  
  
```  
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 Deklaracja `pch2` deklaruje wskaźnik, dzięki któremu można zmodyfikować obiekt stały i dlatego jest niedozwolona. Deklaracja `pch3` określa, że `pointer` jest stałą, a nie obiektem; ta deklaracja jest niedozwolona z tego samego powodu, dla którego niedozwolona jest deklaracja `pch2`.  
  
 Poniższe osiem przypisań pokazuje przypisania poprzez wskaźnik i zmianę wartości wskaźnika dla wcześniejszych deklaracji; na chwilę obecną załóżmy, że inicjalizacja `pch1` poprzez `pch8` była poprawna.  
  
```  
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 Wskaźniki zadeklarowany jako `volatile`, lub jako kombinacja **const** i `volatile`, podlega regułom.  
  
 Wskaźniki do **const** obiekty są często używane w deklaracji funkcji w następujący sposób:  
  
```  
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 Powyższych instrukcji deklaruje funkcję, [strcpy_s —](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), gdzie są dwie z trzech argumentów typu wskaźnika do `char`. Ponieważ argumenty są przekazywane przez odwołanie, a nie wg wartości, funkcja będzie mógł zmodyfikować zarówno `strDestination` i `strSource` Jeśli `strSource` nie zostały zgłoszone jako **const**. Deklaracja `strSource` jako **const** wywołującego gwarantuje, że `strSource` wywołana funkcja nie może zmienić.  
  
> [!NOTE]
>  Ponieważ nie istnieje konwersja standardowa ze *typename* **\*** do **const** *typename* **\***, dozwolone jest przekazywanie argumentu typu **char \***  do [strcpy_s —](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Jednak odwrotnej nie jest PRAWDA. nie istnieje niejawna konwersja do usunięcia **const** atrybutu dla obiekt lub wskaźnik.  
  
 A **const** wskaźnik danego typu można przypisać do tego samego typu wskaźnika. Wskaźnik to jednak nie **const** nie można przypisać do **const** wskaźnika. Poniższy kod pokazuje poprawne i niepoprawne przypisania:  
  
```  
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 Poniższy przykład pokazuje sposób deklarowania obiektu jako const, jeśli posiadasz wskaźnik do wskaźnika do obiektu.  
  
```  
// const_pointer2.cpp  
struct X {  
   X(int i) : m_i(i) { }  
   int m_i;  
};  
  
int main() {  
   // correct  
   const X cx(10);  
   const X * pcx = &cx;  
   const X ** ppcx = &pcx;  
  
   // also correct  
   X const cx2(20);  
   X const * pcx2 = &cx2;  
   X const ** ppcx2 = &pcx2;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wskaźniki](../cpp/pointers-cpp.md)