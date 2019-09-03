---
title: init_seg, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 5e57ea0eedfc1df6e196391c5edd3acfbad0a7c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221005"
---
# <a name="init_seg-pragma"></a>init_seg, pragma

**C++Specjalne**

Określa słowo kluczowe lub kod, który ma wpływ na kolejność, w której jest wykonywany kod uruchomienia.

## <a name="syntax"></a>Składnia

> **#pragma init_seg (** { **kompilator** | **User** **lib** | | "*Nazwa sekcji*" [ **,** *Func-Name* ]} **)**

## <a name="remarks"></a>Uwagi

*Segment* terminów i *sekcja* mają takie samo znaczenie w tym artykule.

Ponieważ kod jest czasami wymagany do zainicjowania globalnych obiektów statycznych, należy określić, kiedy należy skonstruować obiekty. W szczególności ważne jest użycie dyrektywy pragma **init_seg** w bibliotekach dołączanych dynamicznie (dll) lub w bibliotekach, które wymagają inicjalizacji.

Opcje **init_seg** pragma są następujące:

**Compiler**\
Zarezerwowane dla inicjalizacji biblioteki wykonawczej Microsoft C. Obiekty w tej grupie są konstruowane jako pierwsze.

**lib**\
Dostępne dla inicjalizacji dostawców biblioteki klas innych firm. Obiekty w tej grupie są konstruowane po tych, które zostały oznaczone jako **kompilator**, ale przed innymi.

**Użytkownicy**\
Dostępne dla każdego użytkownika. Obiekty w tej grupie są zbudowane jako ostatnie.

*Nazwa sekcji*\
Umożliwia jawne określenie sekcji inicjalizacji. Obiekty w określonej przez użytkownika *nazwie sekcji* nie są konstruowane niejawnie. Jednak ich adresy są umieszczane w sekcji o nazwie *sekcja-Name*.

Podana *Nazwa sekcji* będzie zawierać wskaźniki do funkcji pomocniczych, które będą konstruować obiekty globalne zadeklarowane po pragmie w tym module.

Aby zapoznać się z listą nazw, których nie należy używać podczas tworzenia sekcji, zobacz [/Section](../build/reference/section-specify-section-attributes.md).

*Func-Name*\
Określa funkcję, która ma być wywoływana zamiast `atexit` momentu zakończenia działania programu. Ta funkcja pomocnika wywołuje również [atexit —](../c-runtime-library/reference/atexit.md) ze wskaźnikiem do destruktora dla obiektu globalnego. Jeśli określisz identyfikator funkcji w pragmie formularza,

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

następnie funkcja zostanie wywołana zamiast biblioteki `atexit`wykonawczej C. Umożliwia utworzenie listy destruktorów do wywołania, gdy wszystko jest gotowe do zniszczenia obiektów.

Jeśli konieczne jest odroczenie inicjalizacji (na przykład w bibliotece DLL), można określić nazwę sekcji jawnie. Kod musi następnie wywołać konstruktory dla każdego obiektu statycznego.

Nie ma cudzysłowu otaczającego identyfikator do `atexit` zastąpienia.

Obiekty będą nadal umieszczane w sekcjach zdefiniowanych przez inne `XXX_seg` dyrektywy pragma.

Obiekty, które są zadeklarowane w module nie są automatycznie inicjowane przez czas wykonywania języka C. Kod musi wykonać inicjalizację.

Domyślnie `init_seg` sekcje są tylko do odczytu. Jeśli nazwa sekcji to `.CRT`, kompilator dyskretnie zmienia atrybut na tylko do odczytu, nawet jeśli jest oznaczony jako Odczyt, zapis.

Nie można określić **init_seg** więcej niż raz w jednostce translacji.

Nawet jeśli obiekt nie ma zdefiniowanego przez użytkownika konstruktora, jawnie zdefiniowany w kodzie, kompilator może wygenerować jeden dla siebie. Na przykład może utworzyć jeden, aby powiązać wskaźniki tabeli v. W razie konieczności kod wywołuje konstruktora wygenerowanego przez kompilator.

## <a name="example"></a>Przykład

```cpp
// pragma_directive_init_seg.cpp
#include <stdio.h>
#pragma warning(disable : 4075)

typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors we need to call
PF pfx[200];    // pointers to destructors.

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() { puts("A()"); }
   ~A() { puts("~A()"); }
};

// ctor & dtor called by CRT startup code
// because this is before the pragma init_seg
A aaaa;

// The order here is important.
// Section names must be 8 characters or less.
// The sections with the same name before the $
// are merged into one section. The order that
// they are merged is determined by sorting
// the characters after the $.
// InitSegStart and InitSegEnd are used to set
// boundaries so we can find the real functions
// that we need to call for initialization.

#pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;

#pragma section(".mine$z",read)
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;

// The comparison for 0 is important.
// For now, each section is 256 bytes. When they
// are merged, they are padded with zeros. You
// can't depend on the section being 256 bytes, but
// you can depend on it being padded with zeros.

void InitializeObjects () {
   const PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x) (*x)();
}

void DestroyObjects () {
   while (cxpf>0) {
      --cxpf;
      (pfx[cxpf])();
   }
}

// by default, goes into a read only section
#pragma init_seg(".mine$m", myexit)

A bbbb;
A cccc;

int main () {
   InitializeObjects();
   DestroyObjects();
}
```

```Output
A()
A()
A()
~A()
~A()
~A()
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
