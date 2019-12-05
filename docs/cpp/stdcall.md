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
ms.openlocfilehash: df753241c093db75202a10b106631ce36cf73379
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857284"
---
# <a name="__stdcall"></a>__stdcall

Konwencja wywoływania **__stdcall** jest używana do wywoływania funkcji Win32 API. Wywoływany czyści stos, dzięki czemu kompilator tworzy `vararg` funkcje **__cdecl**. Funkcje korzystające z tej konwencja wywoływania wymagają prototypu funkcji. Modyfikator **__stdcall** jest specyficzny dla firmy Microsoft.

## <a name="syntax"></a>Składnia

> *Typ zwracany* **\_\_stdcall** *funkcji-Name*[ **(** *Lista argumentów* **)** ]

## <a name="remarks"></a>Uwagi

Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Implementacja|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Konwencji przekazywania argumentów|Według wartości, chyba że przekazany jest typ wskaźnika lub odwołania.|
|Odpowiedzialność za utrzymanie stosu|Wywołana funkcja wyciąga argumenty ze stosu.|
|Konwencja dekorowania nazw|Podkreślenie (_) poprzedza nazwę. Za nazwą następuje znak (@) a za nim liczba bajtów (w zapisie dziesiętnym) na liście argumentów. W związku z tym, funkcja zadeklarowana jako `int func( int a, double b )` jest oznaczona: `_func@12`|
|Konwencja translacji wielkości liter|Brak|

Opcja kompilatora [/GZ](../build/reference/gd-gr-gv-gz-calling-convention.md) określa **__stdcall** dla wszystkich funkcji, które nie są jawnie zadeklarowane przy użyciu innej konwencji wywoływania.

W celu zapewnienia zgodności z poprzednimi wersjami **_stdcall** jest synonimem dla **__stdcall** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

Funkcje zadeklarowane za pomocą modyfikatora **__stdcall** zwracają wartości tak samo jak funkcje zadeklarowane przy użyciu [__cdecl](../cpp/cdecl.md).

W przypadku procesorów ARM i x64 **__stdcall** jest akceptowana i ignorowana przez kompilator; w przypadku architektur ARM i x64 według Konwencji argumenty są przesyłane w rejestrach, gdy jest to możliwe, a kolejne argumenty są przesyłane na stosie.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Biorąc pod uwagę tę definicję klasy,

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

jest równoważne do

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Przykład

W poniższym przykładzie użycie **__stdcall** powoduje, że wszystkie typy funkcji `WINAPI` są obsługiwane jako wywołania standardowe:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)