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
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371567"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** jest domyślną konwencją wywoływania dla programów C i C++. Ponieważ stos jest czyszczony przez obiektu wywołującego, może wykonywać `vararg` funkcje. Konwencja wywoływania **__cdecl** tworzy większe pliki wykonywalne niż [__stdcall](../cpp/stdcall.md), ponieważ wymaga, aby każde wywołanie funkcji zawierało kod oczyszczania stosu. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania. Modyfikator **__cdecl** jest specyficzny dla firmy Microsoft.

|Element|Wdrażanie|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Odpowiedzialność za utrzymanie stosu|Funkcja wywołująca pobiera argumenty ze stosu.|
|Konwencja dekorowania nazw|Znak podkreślenia (_) jest poprzedzony nazwami, z wyjątkiem sytuacji, gdy \_eksportowane są _cdecl funkcje korzystające z powiązania C.|
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|

> [!NOTE]
> Aby uzyskać powiązane informacje, zobacz [Nazwy dekoracyjne.](../build/reference/decorated-names.md)

Umieść **modyfikator __cdecl** przed zmienną lub nazwą funkcji. Ponieważ konwencje nazewnictwa i wywoływania języka C są **__cdecl** domyślne, tylko wtedy, gdy należy użyć `/Gv` __cdecl w kodzie x86, jest określenie opcji kompilatora (vectorcall), `/Gz` (stdcall) lub `/Gr` (fastcall). Opcja kompilatora [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) wymusza konwencję wywoływania **__cdecl.**

Na procesorach ARM i x64 **__cdecl** jest akceptowany, ale zazwyczaj ignorowany przez kompilator. Przez konwencję na ARM i x64, argumenty są przekazywane w rejestrach, jeżeli jest to możliwe, a pozostałe argumenty są przekazywane na stosie. W kodzie x64 użyj **__cdecl,** aby zastąpić opcję kompilatora **/Gv** i użyj domyślnej konwencji wywoływania x64.

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

W celu zapewnienia zgodności z poprzednimi wersjami **cdecl** i **_cdecl** są synonimem **__cdecl** chyba że określono opcję kompilatora [ \(/Za Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>Przykład

W poniższym przykładzie kompilator jest poinstruowany, aby używać `system` c nazewnictwa i wywoływania konwencji dla funkcji.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Zobacz też

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
