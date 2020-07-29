---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: 85d1b29fddece741aa94364bb6edfdf3b973faaf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213180"
---
# <a name="__stdcall"></a>__stdcall

**`__stdcall`** Konwencja wywoływania jest używana do wywoływania funkcji Win32 API. Wywoływany czyści stos, dzięki czemu kompilator tworzy `vararg` funkcje **`__cdecl`** . Funkcje, które używają tej konwencji wywoływania, wymagają prototypu funkcji. **`__stdcall`** Modyfikator jest specyficzny dla firmy Microsoft.

## <a name="syntax"></a>Składnia

> *Typ zwracany* **`__stdcall`** *Function-Name*[ **`(`** *Lista argumentów* **`)`** ]

## <a name="remarks"></a>Uwagi

Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Implementacja|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Konwencja przekazywania argumentów|Według wartości, chyba że przeszedł typ wskaźnika lub odwołania.|
|Odpowiedzialność za utrzymanie stosu|Wywoływana funkcja pop własne argumenty ze stosu.|
|Konwencja dekorowania nazw|Podkreślenie ( `_` ) jest poprzedzone nazwą. Po nazwie następuje znak ( `@` ), po którym następuje liczba bajtów (w zapisie dziesiętnym) na liście argumentów. W związku z tym, Funkcja zadeklarowana jako `int func( int a, double b )` ma następujący:`_func@12`|
|Konwencja translacji wielkości liter|Brak|

Opcja kompilatora [/GZ](../build/reference/gd-gr-gv-gz-calling-convention.md) określa **`__stdcall`** dla wszystkich funkcji, które nie są jawnie zadeklarowane przy użyciu innej konwencji wywoływania.

W celu zapewnienia zgodności z poprzednimi wersjami, **`_stdcall`** jest synonimem, **`__stdcall`** Jeśli opcja kompilatora [ `/Za` \( disable rozszerzenia języka](../build/reference/za-ze-disable-language-extensions.md) nie jest określona.

Funkcje zadeklarowane za pomocą **`__stdcall`** modyfikatora zwracają wartości w taki sam sposób jak funkcje zadeklarowane za pomocą [`__cdecl`](../cpp/cdecl.md) .

W przypadku procesorów ARM i x64 program **`__stdcall`** jest akceptowany i ignorowany przez kompilator; w przypadku ARCHITEKTUR ARM i x64 według Konwencji argumenty są przesyłane w rejestrach, gdy jest to możliwe, a kolejne argumenty są przesyłane na stosie.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Uwzględniając tę definicję klasy,

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

jest równoważne z tym

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Przykład

W poniższym przykładzie użyto **`__stdcall`** wyników we wszystkich `WINAPI` typach funkcji, które są obsługiwane jako wywołania standardowe:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
