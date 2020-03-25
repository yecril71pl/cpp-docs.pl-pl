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
ms.openlocfilehash: 3abd1d020e4181a42a7bc38319e5e17e69ef0507
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178544"
---
# <a name="__stdcall"></a>__stdcall

Konwencja wywoływania **__stdcall** jest używana do wywoływania funkcji Win32 API. Wywoływany czyści stos, dzięki czemu kompilator tworzy `vararg` funkcje **__cdecl**. Funkcje, które używają tej konwencji wywoływania, wymagają prototypu funkcji. Modyfikator **__stdcall** jest specyficzny dla firmy Microsoft.

## <a name="syntax"></a>Składnia

> *Typ zwracany* **\_\_stdcall** *funkcji-Name*[ **(** *Lista argumentów* **)** ]

## <a name="remarks"></a>Uwagi

Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Wdrażanie|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Konwencja przekazywania argumentów|Według wartości, chyba że przeszedł typ wskaźnika lub odwołania.|
|Odpowiedzialność za utrzymanie stosu|Wywoływana funkcja pop własne argumenty ze stosu.|
|Konwencja dekorowania nazw|Podkreślenie (_) jest poprzedzone nazwą. Po nazwie następuje znak (@), po którym następuje liczba bajtów (w zapisie dziesiętnym) na liście argumentów. W związku z tym, Funkcja zadeklarowana jako `int func( int a, double b )` ma następujący: `_func@12`|
|Konwencja translacji wielkości liter|None|

Opcja kompilatora [/GZ](../build/reference/gd-gr-gv-gz-calling-convention.md) określa **__stdcall** dla wszystkich funkcji, które nie są jawnie zadeklarowane przy użyciu innej konwencji wywoływania.

W celu zapewnienia zgodności z poprzednimi wersjami **_stdcall** jest synonimem dla **__stdcall** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) .

Funkcje zadeklarowane za pomocą modyfikatora **__stdcall** zwracają wartości tak samo jak funkcje zadeklarowane przy użyciu [__cdecl](../cpp/cdecl.md).

W przypadku procesorów ARM i x64 **__stdcall** jest akceptowana i ignorowana przez kompilator; w przypadku architektur ARM i x64 według Konwencji argumenty są przesyłane w rejestrach, gdy jest to możliwe, a kolejne argumenty są przesyłane na stosie.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Uwzględniając tę definicję klasy,

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

względem tego ruchu

```cpp
void CMyClass::mymethod() { return; }
```

jest równoważne z tym

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

## <a name="see-also"></a>Zobacz też

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
