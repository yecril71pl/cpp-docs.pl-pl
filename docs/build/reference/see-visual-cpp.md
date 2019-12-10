---
title: '&lt;Zobacz > (C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: 8693646fa37648d1b20c791d99d159f2c81b8ec1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988615"
---
# <a name="ltseegt"></a>&lt;Zobacz&gt;

\<Zobacz > tag pozwala określić łącze z poziomu tekstu. Użyj [\<seealso — >](seealso-visual-cpp.md) , aby wskazać tekst, który może być wyświetlany w sekcji Zobacz też.

## <a name="syntax"></a>Składnia

```
<see cref="member"/>
```

#### <a name="parameters"></a>Parametry

*członkiem*<br/>
Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.  Ujmij nazwę w pojedyncze lub podwójne cudzysłowy.

Kompilator sprawdza, czy dany element kodu istnieje i rozwiązuje `member` do nazwy elementu w wyjściowym kodzie XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

Zobacz [\<podsumowanie >](summary-visual-cpp.md) , aby zobaczyć przykład użycia \<>.

Kompilator MSVC podejmie próbę rozpoznania odwołań cref w jednym przejściu poprzez Komentarze do dokumentacji.  W związku z tym, C++ w przypadku używania reguł odnośników nie znaleziono symbolu przez kompilator, odwołanie zostanie oznaczone jako nierozwiązane. Aby uzyskać więcej informacji, zobacz [\<seealso — >](seealso-visual-cpp.md) .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak można utworzyć odwołanie cref do typu ogólnego, takiego jak kompilator rozpozna odwołanie.

```cpp
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
