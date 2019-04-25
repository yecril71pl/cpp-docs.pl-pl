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
ms.openlocfilehash: 298485d310ee4039b13781a8b5cd88a489af3b8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232405"
---
# <a name="cdecl"></a>__cdecl

**Microsoft Specific**

**__cdecl** jest domyślną konwencję wywoływania dla języka C i C++ programów. Ponieważ stos jest czyszczony przez obiekt wywołujący, można wykonać `vararg` funkcji. **__Cdecl** konwencji wywoływania tworzy większe pliki wykonywalne niż [__stdcall](../cpp/stdcall.md), ponieważ wymaga, aby każde wywołanie funkcji kod porządkujący stosu. Na poniższej liście przedstawiono implementację niniejszej konwencji wywoływania.

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