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
ms.openlocfilehash: bfa468c96196c417415801239925707c43a49c4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178681"
---
# <a name="__sptr-__uptr"></a>__sptr, __uptr

**Specyficzne dla firmy Microsoft**

Użyj modyfikatora **__sptr** lub **__uptr** w deklaracji 32-bitowego wskaźnika, aby określić sposób, w jaki kompilator konwertuje wskaźnik 32-bitowy na wskaźnik 64-bitowy. Wskaźnik 32-bitowy jest konwertowany, na przykład gdy jest przypisany do zmiennej wskaźnika 64-bitowego lub wyłuskany na platformie 64-bitowej.

Dokumentacja obsługi technicznej Microsoft dla 64-bitowych platform czasami dotyczy najważniejszego bitu wskaźnika 32-bitowego, jako bitu znaku. Domyślnie kompilator używa rozszerzenia znaku, aby konwertować wskaźnik 32-bitowy na wskaźnik 64-bitowy. Oznacza to, że najmniej znaczące 32 bity wskaźnika 64-bitowego są ustawione na wartość wskaźnika 32-bitowego i najbardziej znaczące 32 bity są ustawione na wartość bitu znaku wskaźnika 32-bitowego. Ta konwersja daje poprawne wyniki, jeśli bit znaku ma wartość 0, ale nie jeśli bitem znaku jest 1. Na przykład 32-bitowy adres 0x7FFFFFFF daje równoważny 64-bitowy adres 0x000000007FFFFFFF, ale 32-bitowy adres 0x80000000 zostanie niepoprawnie zmieniony na 0xFFFFFFFF80000000.

**__Sptr**lub podpisany wskaźnik, modyfikator określa, że konwersja wskaźnika ustawia najbardziej znaczące bity wskaźnika 64-bitowego na bit znaku 32-bitowego wskaźnika. Modyfikator **__uptr**lub bez znaku określa, że konwersja ustawia najbardziej znaczące bity na zero. Następujące deklaracje pokazują Modyfikatory **__sptr** i **__uptr** używane z dwoma niekwalifikowanymi wskaźnikami, dwa wskaźniki kwalifikowana z typem [__ptr32](../cpp/ptr32-ptr64.md) i parametrem funkcji.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

Użyj modyfikatorów **__sptr** i **__uptr** z deklaracjami wskaźnika. Użyj modyfikatorów w położeniu [kwalifikatora typu wskaźnika](../c-language/pointer-declarations.md), co oznacza, że modyfikator musi następować przy użyciu gwiazdki. Nie można używać modyfikatorów ze [wskaźnikami do elementów członkowskich](../cpp/pointers-to-members.md). Modyfikatory nie wpływają na deklaracje niewskaźnikowe.

W celu zapewnienia zgodności z poprzednimi wersjami **_sptr** i **_uptr** są synonimami **__sptr** i **__uptr** , chyba że opcja kompilatora [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Przykład

Poniższy przykład deklaruje 32-bitowe wskaźniki używające modyfikatorów **__sptr** i **__uptr** , przypisuje każdy wskaźnik 32-bitowy do zmiennej wskaźnika 64-bit, a następnie wyświetla wartość szesnastkową każdego wskaźnika 64-bitowego. Przykład jest kompilowany za pomocą natywnego 64-bitowego kompilatora i jest wykonywany na platformie 64-bitowej.

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)
