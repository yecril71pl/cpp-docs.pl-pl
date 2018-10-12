---
title: __stdcall | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
dev_langs:
- C++
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06eafcd4303e01be523554f2a164e6cb14f79a26
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162259"
---
# <a name="stdcall"></a>__stdcall

**Microsoft Specific**

**__Stdcall** konwencji wywoływania służy do wywoływania funkcji Win32 API. Wywoływany obiekt czyści stos, dzięki czemu sprawia, że kompilator `vararg` funkcje **__cdecl**. Funkcje korzystające z tej Konwencja wywoływania wymagają prototypu funkcji.

## <a name="syntax"></a>Składnia

> *zwracany typ*  **\_ \_stdcall** *nazwy funkcji*[**(** *listy argumentów* **)** ]

## <a name="remarks"></a>Uwagi

Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Implementacja|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Konwencji przekazywania argumentów|Według wartości chyba że przekazany jest typ wskaźnika lub odwołania.|
|Odpowiedzialność za utrzymanie stosu|Wywołana funkcja wyciąga argumenty ze stosu.|
|Konwencja dekorowania nazw|Podkreślenie (_) jest poprzedzana nazwy. Nazwą następuje znak (@) następuje liczba bajtów (w zapisie dziesiętnym na liście argumentów). W związku z tym, funkcja zadeklarowana jako `int func( int a, double b )` zostanie nadany w następujący sposób: `_func@12`|
|Konwencja translacji wielkości liter|Brak|

[GZ](../build/reference/gd-gr-gv-gz-calling-convention.md) określa — opcja kompilatora **__stdcall** dla wszystkich funkcji, które nie zostały jawnie zadeklarowane z inną Konwencją wywoływania.

W celu zgodności z poprzednimi wersjami **_stdcall** jest synonimem dla **__stdcall** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

Funkcje zadeklarowane za pomocą **__stdcall** modyfikator zwracanej wartości w taki sam sposób jak funkcje zadeklarowane za pomocą [__cdecl](../cpp/cdecl.md).

Na ARM i x64 procesorów, **__stdcall** jest akceptowane i ignorowane przez kompilator; na ARM i x64 architektury, według Konwencji argumenty są przekazywane w rejestrach, jeżeli jest to możliwe, a następne argumenty są przekazywane na stosie.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Biorąc pod uwagę tę definicję klasy

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

jest to równoważne

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Przykład

W poniższym przykładzie użycie **__stdcall** powoduje we wszystkich `WINAPI` typy funkcji, są traktowane jako standardowe wywołanie:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)