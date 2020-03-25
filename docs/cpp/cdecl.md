---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: 8f2b2b0cea8ff30cc450aae534fbff0d7b77f457
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190102"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** jest domyślną konwencją wywoływania dla C i C++ programów. Ponieważ stos jest czyszczony przez obiekt wywołujący, może `vararg` funkcje. Konwencja wywoływania **__cdecl** tworzy większe pliki wykonywalne niż [__stdcall](../cpp/stdcall.md), ponieważ wymaga, aby każde wywołanie funkcji obejmowało kod czyszczący stosu. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania. Modyfikator **__cdecl** jest specyficzny dla firmy Microsoft.

|Element|Wdrażanie|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Odpowiedzialność za utrzymanie stosu|Funkcja wywołująca pobiera argumenty ze stosu.|
|Konwencja dekorowania nazw|Znak podkreślenia (_) jest poprzedzony nazwami, z wyjątkiem tego, że eksportowane są \__cdecl funkcji, które używają połączenia C.|
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|

> [!NOTE]
>  Aby uzyskać powiązane informacje, zobacz [nazwy dekoracyjne](../build/reference/decorated-names.md).

Umieść modyfikator **__cdecl** przed zmienną lub nazwą funkcji. Ponieważ nazewnictwo C i konwencje wywoływania są domyślne, Jedynym wymaganiem **__cdecl** w kodzie x86 jest, gdy określono opcję kompilatora `/Gv` (vectorcall), `/Gz` (stdcall) lub `/Gr` (fastcall). Opcja kompilatora [/GD](../build/reference/gd-gr-gv-gz-calling-convention.md) wymusza konwencję wywoływania **__cdecl** .

W przypadku procesorów ARM i x64 **__cdecl** jest akceptowany, ale zazwyczaj ignorowany przez kompilator. Przez konwencję na ARM i x64, argumenty są przekazywane w rejestrach, jeżeli jest to możliwe, a pozostałe argumenty są przekazywane na stosie. W kodzie x64 Użyj **__cdecl** , aby zastąpić opcję kompilatora **/GV** i użyć domyślnej konwencji wywoływania x64.

W przypadku funkcji niestatycznych klas, jeśli funkcja jest zdefiniowana poza wierszem, modyfikator konwencji wywoływania nie musi być określony w definicji poza wierszem. Oznacza to, że dla metod niestatycznej składowej klasy przyjmowana jest konwencja wywoływania określona podczas deklaracji w punkcie definicji. Biorąc pod uwagę tę definicję klasy:

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

to:

```cpp
void CMyClass::mymethod() { return; }
```

jest równoważne temu:

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

Aby zapewnić zgodność z poprzednimi wersjami, **CDECL** i **_cdecl** są synonimem dla **__cdecl** , chyba że opcja kompilatora [/za \(Disable Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Przykład

W poniższym przykładzie kompilator jest zobowiązany do używania konwencji nazewnictwa języka C i konwencje wywoływania dla funkcji `system`.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Zobacz też

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
