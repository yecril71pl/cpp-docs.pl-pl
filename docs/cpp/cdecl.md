---
title: __cdecl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
dev_langs:
- C++
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 085d8a49ed3c66f96bf8c2b8bdae7ca54cf3bef6
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163780"
---
# <a name="cdecl"></a>__cdecl

**Microsoft Specific**

**__cdecl** jest domyślna konwencja wywołania dla programów C i C++. Ponieważ stos jest czyszczony przez obiekt wywołujący, można wykonać `vararg` funkcji. **__Cdecl** konwencji wywoływania tworzy większe pliki wykonywalne niż [__stdcall](../cpp/stdcall.md), ponieważ wymaga, aby każde wywołanie funkcji kod porządkujący stosu. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

|Element|Implementacja|
|-------------|--------------------|
|Kolejność przekazywania argumentów|Od prawej do lewej.|
|Odpowiedzialność za utrzymanie stosu|Funkcja wywołująca pobiera argumenty ze stosu.|
|Konwencja dekorowania nazw|Znak podkreślenia (_) jest umieszczany przez nazwami, z wyjątkiem sytuacji, gdy \__cdecl funkcje, które używają połączenia są eksportowane.|
|Konwencja translacji wielkości liter|Translacja wielkości liter nie jest wykonywana.|

> [!NOTE]
>  Aby uzyskać powiązane informacje, zobacz [nazwy dekorowane](../build/reference/decorated-names.md).

Miejsce **__cdecl** modyfikator przed zmienną lub nazwą funkcji. Ponieważ nazewnictwo C i Konwencje wywoływania są domyślne tylko wtedy należy użyć **__cdecl** w x86 kod jest po określeniu `/Gv` (vectorcall), `/Gz` (stdcall) lub `/Gr` (fastcall) — Opcja kompilatora. [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) wymusza — opcja kompilatora **__cdecl** konwencji wywoływania.

Na ARM i x64 procesorów, **__cdecl** jest akceptowana, ale zazwyczaj są ignorowane przez kompilator. Przez konwencję na ARM i x64, argumenty są przekazywane w rejestrach, jeżeli jest to możliwe, a pozostałe argumenty są przekazywane na stosie. W x64 kodu, należy użyć **__cdecl** do zastąpienia **GV** — opcja kompilatora i użyj domyślnej x64 konwencji wywoływania.

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

Dla zgodności z poprzednimi wersjami **cdecl** i **_cdecl** jest synonimem **__cdecl** chyba że — opcja kompilatora [/Za \(wyłączyć rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określony.

## <a name="example"></a>Przykład

W poniższym przykładzie kompilator jest zobowiązany do używania konwencji nazewnictwa i konwencji wywoływania `system` funkcji.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Zobacz także

[Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)