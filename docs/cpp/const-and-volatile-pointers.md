---
title: const i volatile, wskaźniki
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: a8fd25777d1169ba281fbee173c1c8f5673c8b56
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227572"
---
# <a name="const-and-volatile-pointers"></a>const i volatile, wskaźniki

Słowa kluczowe [const](const-cpp.md) i [volatile](volatile-cpp.md) zmieniają sposób traktowania wskaźników. **`const`** Słowo kluczowe Określa, że wskaźnik nie może być modyfikowany po inicjacji; wskaźnik jest chroniony przed modyfikacją.

**`volatile`** Słowo kluczowe Określa, że wartość skojarzona z nazwą poniższą może być modyfikowana przez akcje inne niż te w aplikacji użytkownika. Dlatego **`volatile`** słowo kluczowe jest przydatne w przypadku deklarowania obiektów w pamięci współdzielonej, do których można uzyskać dostęp przez wiele procesów lub globalnych obszarów danych używanych do komunikacji z procedurami usługi przerwania.

Gdy nazwa jest zadeklarowana jako **`volatile`** , kompilator ponownie ładuje wartość z pamięci za każdym razem, gdy uzyskuje do niej dostęp za pomocą programu. Zmniejsza to znacznie możliwości optymalizacji. Jednakże, gdy stan obiektu może ulegać nieoczekiwanym zmianom, jest to jedyny sposób zapewnienia przewidywalnej wydajności programu.

Aby zadeklarować obiekt wskazywany przez wskaźnik jako **`const`** lub **`volatile`** , użyj deklaracji w postaci:

```cpp
const char *cpch;
volatile char *vpch;
```

Aby zadeklarować wartość wskaźnika — czyli rzeczywisty adres przechowywany we wskaźniku — jako **`const`** lub **`volatile`** , użyj deklaracji w postaci:

```cpp
char * const pchc;
char * volatile pchv;
```

Język C++ uniemożliwia przypisania, które mogłyby umożliwić modyfikację obiektu lub wskaźnika zadeklarowanego jako **`const`** . Takie przypisania powodowałyby usunięcie informacji, z którą obiekt lub wskaźnik został zadeklarowany, naruszając w ten sposób zamiar pierwotnej deklaracji. Rozważ następujące deklaracje:

```cpp
const char cch = 'A';
char ch = 'B';
```

Uwzględniając poprzednie deklaracje dwóch obiektów ( `cch` typu **const char**i `ch` typu **Char)**, następująca deklaracja/inicjalizacje są prawidłowe:

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

Deklaracja `pch2` deklaruje wskaźnik, dzięki któremu można zmodyfikować obiekt stały i dlatego jest niedozwolona. Deklaracja `pch3` określa, że wskaźnik jest stałą, a nie obiektem; deklaracja jest niedozwolona z tego samego powodu, gdy `pch2` Deklaracja jest niedozwolona.

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

Wskaźniki zadeklarowane jako **`volatile`** , lub w postaci mieszanki **`const`** i **`volatile`** , przestrzegają tych samych reguł.

Wskaźniki do **`const`** obiektów często są używane w deklaracjach funkcji w następujący sposób:

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

Poprzednia instrukcja deklaruje funkcję, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), gdzie dwa z trzech argumentów są typu wskaźnika do **`char`** . Ponieważ argumenty są przekazane przez odwołanie, a nie przez wartość, funkcja ta może być wolna do modyfikacji `strDestination` i `strSource` Jeśli `strSource` nie zostały zadeklarowane jako **`const`** . Deklaracja `strSource` AS **`const`** gwarantuje obiekt wywołujący, który `strSource` nie może zostać zmieniony przez wywołaną funkcję.

> [!NOTE]
> Ponieważ istnieje konwersja standardowa z *TypeName* <strong>\*</strong> do **`const`** *TypeName* <strong>\*</strong> , można przekazać argument typu `char *` do [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Jednak odwrócenie nie jest prawdziwe; nie istnieje niejawna konwersja, aby usunąć **`const`** atrybut z obiektu lub wskaźnika.

**`const`** Wskaźnik danego typu może być przypisany do wskaźnika tego samego typu. Jednak wskaźnik, który nie **`const`** może być przypisany do **`const`** wskaźnika. Poniższy kod pokazuje poprawne i niepoprawne przypisania:

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

[Wskaźniki](pointers-cpp.md) 
 [Surowe wskaźniki](raw-pointers.md)
