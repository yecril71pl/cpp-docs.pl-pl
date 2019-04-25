---
title: __sptr, __uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: 957f744ca6c5a7be807c1dc68fcd2b602b72300e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330962"
---
# <a name="sptr-uptr"></a>__sptr, __uptr

**Microsoft Specific**

Użyj **__sptr —** lub **__uptr —** modyfikatora w deklaracji wskaźnika 32-bitowego, aby określić, jak kompilator konwertuje wskaźnik 32-bitowy na wskaźnik 64-bitowych. Wskaźnik 32-bitowy jest konwertowany, na przykład gdy jest przypisany do zmiennej wskaźnika 64-bitowego lub wyłuskany na platformie 64-bitowej.

Dokumentacja obsługi technicznej Microsoft dla 64-bitowych platform czasami dotyczy najważniejszego bitu wskaźnika 32-bitowego, jako bitu znaku. Domyślnie kompilator używa rozszerzenia znaku, aby konwertować wskaźnik 32-bitowy na wskaźnik 64-bitowy. Oznacza to, że najmniej znaczące 32 bity wskaźnika 64-bitowego są ustawione na wartość wskaźnika 32-bitowego i najbardziej znaczące 32 bity są ustawione na wartość bitu znaku wskaźnika 32-bitowego. Ta konwersja daje poprawne wyniki, jeśli bit znaku ma wartość 0, ale nie jeśli bitem znaku jest 1. Na przykład 32-bitowy adres 0x7FFFFFFF daje równoważny 64-bitowy adres 0x000000007FFFFFFF, ale 32-bitowy adres 0x80000000 zostanie niepoprawnie zmieniony na 0xFFFFFFFF80000000.

**__Sptr —**, lub wskaźnik, oznaczony modyfikator Określa, że konwersja wskaźnika ustawia najbardziej znaczące bity wskaźnika 64-bitowego na bit znaku wskaźnika 32-bitowego. **__Uptr —**, lub wskaźnik nieoznaczony modyfikator Określa, że konwersja ustawi najbardziej znaczące bity na wartość zero. Następujące deklaracje pokazują **__sptr —** i **__uptr —** modyfikatorów używane z dwoma niekwalifikowanymi wskaźnikami, dwoma wskaźnikami kwalifikowanymi za pomocą [__ptr32](../cpp/ptr32-ptr64.md) typ i funkcję parametr.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

Użyj **__sptr —** i **__uptr —** Modyfikatory z deklaracjami wskaźników. Modyfikatorów należy używać w pozycji [kwalifikatora typu wskaźnika](../c-language/pointer-declarations.md), co oznacza, że modyfikator musi wystąpić po gwiazdce. Nie można używać modyfikatorów z [wskaźników do elementów członkowskich](../cpp/pointers-to-members.md). Modyfikatory nie wpływają na deklaracje niewskaźnikowe.

W celu zgodności z poprzednimi wersjami **_sptr** i **_uptr** są synonimy **__sptr —** i **__uptr —** , chyba że —opcjakompilatora[/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określony.

## <a name="example"></a>Przykład

Poniższy przykład deklaruje 32-bitowych wskaźników, które używają **__sptr —** i **__uptr —** modyfikatorów, przypisuje każdego wskaźnika 32-bitowego do zmiennej wskaźnika 64-bitowego, a następnie wyświetla wartość szesnastkową każdego 64 - bitowy wskaźnik. Przykład jest kompilowany za pomocą natywnego 64-bitowego kompilatora i jest wykonywany na platformie 64-bitowej.

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)