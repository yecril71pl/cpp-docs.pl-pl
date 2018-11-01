---
title: __fastcall
ms.date: 10/09/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: 19cc8efb98660e8cdb3f6d9b03f0b7bd85a34949
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480044"
---
# <a name="fastcall"></a>__fastcall

**Microsoft Specific**

**__Fastcall** konwencji wywoływania Określa, że argumenty funkcji są przekazywane do rejestrów, gdy jest to możliwe. Ta konwencja wywoływania dotyczy tylko x86 architektury. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Implementacja|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Pierwsze dwa argumenty DWORD lub mniejsze argumenty znalezione na liście argumentów od lewej do prawej są przekazywane w rejestrach ECX i EDX; wszystkie inne argumenty są przekazywane na stosie od prawej do lewej.|
|Odpowiedzialność za utrzymanie stosu|Wywołana funkcja wyciąga argumenty ze stosu.|
|Konwencja dekorowania nazw|Znak (\@) stanowi prefiks do nazw; znakiem następuje liczba bajtów (w zapisie dziesiętnym) w parametrze umieszczona jako sufiks do nazw.|
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|

> [!NOTE]
>  Przyszłe wersje kompilatora mogą używać innych rejestrów do przechowywania parametrów.

Za pomocą [GR](../build/reference/gd-gr-gv-gz-calling-convention.md) — opcja kompilatora powoduje, że każda funkcja w module jest skompilowana jako **__fastcall** chyba że funkcja jest zadeklarowana przez użycie z atrybutem sprzecznych lub nazwą funkcji jest `main` .

**__Fastcall** — słowo kluczowe jest akceptowane i ignorowane przez kompilatory, których platformą docelową ARM i x64 architektury; x64 mikroukładu, według Konwencji pierwsze cztery argumenty są przekazywane w rejestrach, jeżeli jest to możliwe, a dodatkowe argumenty są przekazywane na stosie. Aby uzyskać więcej informacji, zobacz [Przegląd x64 Konwencje wywoływania](../build/overview-of-x64-calling-conventions.md). W układzie ARM maksymalnie cztery liczby całkowitej argumentów i osiem argumentów zmiennoprzecinkowych może być przekazywane w rejestrach, a dodatkowe argumenty są przekazywane na stosie.

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

W celu zgodności z poprzednimi wersjami **_fastcall** jest synonimem dla **__fastcall** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

## <a name="example"></a>Przykład

W poniższym przykładzie funkcja `DeleteAggrWrapper` jest przekazywana argumentom w rejestrach:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)