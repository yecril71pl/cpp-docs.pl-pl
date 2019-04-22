---
title: init_seg
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.init_seg
- init_seg_CPP
helpviewer_keywords:
- pragmas, init_seg
- init_seg pragma
- data segment initializing [C++]
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
ms.openlocfilehash: 801496739fd9bd2b8a14e699ca4da9fe79f3a28d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026634"
---
# <a name="initseg"></a>init_seg

**Określonego język C++**

Określa sekcję — słowo kluczowe lub kod, który wpływa na kolejność, w której uruchamiania kod jest wykonywany.

## <a name="syntax"></a>Składnia

```
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )
```

## <a name="remarks"></a>Uwagi

Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.

Ponieważ inicjowania statycznych obiektów globalnych może obejmować wykonywanie kodu, należy określić słowo kluczowe, które określa, kiedy obiekty mają być zbudowane. Jest to szczególnie ważne użyć **init_seg** pragmy w bibliotekach dołączanych dynamicznie (dll) lub konieczności inicjowania biblioteki.

Opcje **init_seg** pragma są:

*compiler*<br/>
Zarezerwowane dla inicjowania biblioteki wykonawczej C firmy Microsoft. Obiekty w tej grupie są konstruowane najpierw.

*lib*<br/>
Dostępne dla inicjowania biblioteki klas w innych dostawców. Obiekty w tej grupie są konstruowane, po oznaczone jako *kompilatora* , ale przed wszystkie inne pola.

*Użytkownik*<br/>
Dostępne dla każdego użytkownika. Obiekty w tej grupie są konstruowane ostatnio.

*Nazwa sekcji* umożliwia jawne określenie sekcji inicjowania. Obiekty w określonych przez użytkownika *nazwa sekcji* nie są niejawnie skonstruowany; jednak ich adresy są umieszczane w sekcji o nazwie określonej przez *nazwa sekcji*.

Nazwa sekcji, które publikujesz będzie zawierać wskaźniki do funkcji pomocnika, które będzie konstruowania obiektów globalnych, zadeklarowanych w tym module po pragmy.

Aby uzyskać listę nazw, nie należy używać podczas tworzenia sekcji, zobacz [/SECTION](../build/reference/section-specify-section-attributes.md).

*Nazwa FUNC* określa funkcję, która ma być wywoływana zamiast `atexit` gdy program zamyka. Ponadto wywołuje tę funkcję Pomocnika [atexit](../c-runtime-library/reference/atexit.md) ze wskaźnikiem do destruktor dla obiektów globalnych. Jeśli określisz identyfikator funkcji w pragmy formularza

```cpp
int __cdecl myexit (void (__cdecl *pf)(void))
```

następnie funkcja będzie wywoływana zamiast biblioteki wykonawczej C `atexit`. Dzięki temu można utworzyć listę destruktorami, które będą muszą zostać wywołane, gdy jesteś gotowy do likwidacji obiektów.

Jeśli potrzebujesz odroczenie inicjowania (na przykład w bibliotece DLL) można jawnie określić nazwę sekcji. Następnie należy wywołać konstruktory dla każdego obiektu statycznego.

Istnieją nie cudzysłowów wokół identyfikator `atexit` zastępczy.

Obiekty nadal zostaną umieszczone w sekcjach zdefiniowane przez inne dyrektywy pragma XXX_seg.

Obiekty, które są zadeklarowane w module nie zostaną automatycznie zainicjowane przez środowiska wykonawczego języka C. Należy zrobić tego samodzielnie.

Domyślnie `init_seg` sekcje są tylko do odczytu. Jeśli nazwa sekcji. CRT, kompilator dyskretnie zmieni atrybutu tylko do odczytu, nawet wtedy, gdy jest ona oznaczona jako odczyt, zapis.

Nie można określić **init_seg** więcej niż jeden raz w jednostce translacji.

Nawet, jeśli obiekt nie ma zdefiniowanych przez użytkownika konstruktora, Konstruktor nie jest jawnie zdefiniowany w kodzie, kompilator może wygenerować (na przykład można powiązać wskaźniki v-table). W związku z tym kod musi wywołać konstruktora generowanych przez kompilator.

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

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)