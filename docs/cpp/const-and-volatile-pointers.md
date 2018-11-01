---
title: Wskaźniki stałe i nietrwałe
ms.date: 11/04/2016
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: c869adbbdc8a5a17d315e64e5ac15545e0c46e26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628192"
---
# <a name="const-and-volatile-pointers"></a>Wskaźniki stałe i nietrwałe

[Const](../cpp/const-cpp.md) i [volatile](../cpp/volatile-cpp.md) słowa kluczowe zmienić sposób traktowania wskaźników. **Const** — słowo kluczowe Określa, że wskaźnik nie może być modyfikowany po inicjalizacji; wskaźnik jest odtąd chroniony przed.

**Volatile** — słowo kluczowe Określa, że wartość skojarzona z nazwą, który następuje po może być modyfikowana przez akcje inne niż te w aplikacji użytkownika. W związku z tym **volatile** — słowo kluczowe jest przydatne do deklarowania obiektów w pamięci współdzielonej, który może zostać oceniony przez wiele procesów lub globalnych obszarów danych używany do komunikacji z procedurami usług przerwania.

Jeśli nazwa jest zadeklarowana jako **volatile**, kompilator ładuje ponownie wartość z pamięci, każdym razem, jest on dostępny w programie. Zmniejsza to znacznie możliwości optymalizacji. Jednakże, gdy stan obiektu może ulegać nieoczekiwanym zmianom, jest to jedyny sposób zapewnienia przewidywalnej wydajności programu.

Aby zadeklarować obiekt wskazywany przez wskaźnik jako **const** lub **volatile**, użyj deklaracji w postaci:

```cpp
const char *cpch;
volatile char *vpch;
```

Aby zadeklarować wartość wskaźnika-czyli rzeczywisty adres przechowywany we wskaźniku — jako **const** lub **volatile**, użyj deklaracji w postaci:

```cpp
char * const pchc;
char * volatile pchv;
```

Język C++ zapobiega przypisaniom, które pozwalałyby na modyfikację obiektu lub wskaźnika zadeklarowanego jako **const**. Takie przypisania powodowałyby usunięcie informacji, z którą obiekt lub wskaźnik został zadeklarowany, naruszając w ten sposób zamiar pierwotnej deklaracji. Rozważ następujące deklaracje:

```cpp
const char cch = 'A';
char ch = 'B';
```

Posiadając wcześniej deklaracje dwóch obiektów (`cch`, typu **const char**, i `ch`, typu **char)**, następująca deklaracja/inicjacje są prawidłowe:

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

Poniższa deklaracja/inicjacje są błędne.

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

Deklaracja `pch2` deklaruje wskaźnik, dzięki któremu można zmodyfikować obiekt stały i dlatego jest niedozwolona. Deklaracja `pch3` Określa, że wskaźnik jest wartością stałą, nie obiektem; ta deklaracja jest niedozwolona z tego samego powodu `pch2` deklaracja jest niedozwolona.

Poniższe osiem przypisań pokazuje przypisania poprzez wskaźnik i zmianę wartości wskaźnika dla wcześniejszych deklaracji; na chwilę obecną załóżmy, że inicjalizacja `pch1` poprzez `pch8` była poprawna.

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

Wskaźniki zadeklarowane jako **volatile**, lub jako kombinację **const** i **volatile**, przestrzegają tych samych zasad.

Wskaźniki do **const** obiekty są często używane w deklaracjach funkcji w następujący sposób:

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

Poprzednia instrukcja deklaruje funkcję, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), gdzie dwa z trzech argumentów są wskaźnikami typu do **char**. Ponieważ argumenty są przekazywane przez odwołanie, a nie przez wartość, funkcja będzie mogła swobodnie modyfikować zarówno `strDestination` i `strSource` Jeśli `strSource` nie zostało zadeklarowane jako **const**. Deklaracja `strSource` jako **const** zapewnia obiekt wywołujący `strSource` nie można zmienić przez wywoływaną funkcję.

> [!NOTE]
> Ponieważ nie istnieje konwersja standardowa ze *typename* <strong>\*</strong> do **const** *typename* <strong>\*</strong>, dozwolone jest przekazanie argumentu typu `char *` do [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Jednakże odwrotna sytuacja nie jest PRAWDA. nie istnieje niejawna konwersja do usunięcia **const** atrybut z obiektu lub wskaźnika.

A **const** wskaźnik danego typu mogą być przypisane do wskaźnika tego samego typu. Jednak wskaźnik nie jest **const** nie można przypisać do **const** wskaźnika. Poniższy kod pokazuje poprawne i niepoprawne przypisania:

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

Poniższy przykład pokazuje sposób deklarowania obiektu jako const, jeśli posiadasz wskaźnik do wskaźnika do obiektu.

```cpp
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

## <a name="see-also"></a>Zobacz także

[Wskaźniki](../cpp/pointers-cpp.md)