---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: 420552dd62c46ab5c2fa7e201387f258617f8453
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227481"
---
# <a name="__fastcall"></a>__fastcall

**Specyficzne dla firmy Microsoft**

**`__fastcall`** Konwencja wywoływania określa, że argumenty funkcji mają być przekazane w rejestrach, jeśli jest to możliwe. Ta konwencja wywoływania dotyczy tylko architektury x86. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Implementacja|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Pierwsze dwa argumenty typu DWORD lub mniejsze, które znajdują się na liście argumentów od lewej do prawej są przekazane w rejestrach ECX i EDX; wszystkie inne argumenty są przesyłane na stosie od prawej do lewej.|
|Odpowiedzialność za utrzymanie stosu|Wywoływana funkcja pop argumenty ze stosu.|
|Konwencja dekorowania nazw|Przy znaku ( \@ ) jest poprzedzony nazwami, a po nim liczba bajtów (w zapisie dziesiętnym) na liście parametrów jest sufiksem do nazw.|
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|

> [!NOTE]
> Przyszłe wersje kompilatora mogą używać różnych rejestrów do przechowywania parametrów.

Użycie opcji kompilatora [/gr](../build/reference/gd-gr-gv-gz-calling-convention.md) powoduje, że każda funkcja w module jest skompilowana jako, **`__fastcall`** chyba że funkcja jest zadeklarowana przy użyciu atrybutu powodującego konflikt lub nazwa funkcji jest `main` .

**`__fastcall`** Słowo kluczowe jest akceptowane i ignorowane przez kompilatory, które obsługują architektury ARM i x64; na mikroukładie x64, według Konwencji, pierwsze cztery argumenty są przesyłane do rejestrów, gdy jest to możliwe, a dodatkowe argumenty są przesyłane na stosie. Aby uzyskać więcej informacji, zobacz [konwencja wywoływania x64](../build/x64-calling-convention.md). Na układzie ARM można przekazywać maksymalnie cztery argumenty całkowite i osiem argumentów zmiennoprzecinkowych w rejestrach, a dodatkowe argumenty są przesyłane na stosie.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Biorąc pod uwagę tę definicję klasy:

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

to:

```cpp
void CMyClass::mymethod() { return; }
```

jest równoważne temu:

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

W celu zapewnienia zgodności z poprzednimi wersjami **_fastcall** jest synonimem, **`__fastcall`** Jeśli nie określono opcji kompilatora [/za \( disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Przykład

W poniższym przykładzie funkcja `DeleteAggrWrapper` jest przenoszona argumentów w rejestrach:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
