---
title: '&lt;zobacz > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: be99d3ac156c587888a7c56997d82531cf86ccec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318904"
---
# <a name="ltseegt"></a>&lt;Zobacz&gt;

\<Zobacz > należy określić łącze między w tekście. Użyj [ \<SeeAlso — >](seealso-visual-cpp.md) do wskazania tekst, który możesz chcieć pojawiają się w sekcji Zobacz też.

## <a name="syntax"></a>Składnia

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parametry

*Element członkowski*<br/>
Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

Kompilator sprawdza, czy dany element kodu istnieje i jest rozpoznawana jako `member` do nazwy elementu w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

Zobacz [ \<podsumowania >](summary-visual-cpp.md) na przykład za pomocą \<zobacz >.

Za pomocą kompilatora MSVC będzie próbował rozpoznać odwołania cref w jednym przebiegu za pomocą komentarzy dokumentacji.  W związku z tym, jeśli przy użyciu reguł wyszukiwania C++, symbolu nie można odnaleźć kompilatora odwołania zostaną oznaczone jako nierozwiązane. Zobacz [ \<SeeAlso — >](seealso-visual-cpp.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wprowadzisz cref odwołanie do typu ogólnego, taki sposób, że kompilator będzie rozpoznać odwołania.

```
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
