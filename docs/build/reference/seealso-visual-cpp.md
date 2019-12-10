---
title: '&lt;seealso — > (C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 698db2df462f561acd897d0d0e56b3106a915466
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988604"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

Tag \<seealso — > umożliwia określenie tekstu, który ma być wyświetlany w sekcji Zobacz też. Użyj [\<zobacz >](see-visual-cpp.md) , aby określić łącze z tekstu.

## <a name="syntax"></a>Składnia

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parametry

*członkiem*<br/>
Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.  Ujmij nazwę w pojedyncze lub podwójne cudzysłowy.

Kompilator sprawdza, czy dany element kodu istnieje i rozwiązuje `member` do nazwy elementu w wyjściowym kodzie XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [\<see >](see-visual-cpp.md).

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

Zobacz [\<podsumowanie >](summary-visual-cpp.md) , aby uzyskać przykład użycia \<seealso — >.

Kompilator MSVC podejmie próbę rozpoznania odwołań cref w jednym przejściu poprzez Komentarze do dokumentacji.  W związku z tym, C++ w przypadku używania reguł odnośników nie znaleziono symbolu przez kompilator, odwołanie zostanie oznaczone jako nierozwiązane.

## <a name="example"></a>Przykład

W poniższym przykładzie odwołuje się do nierozpoznanego symbolu w cref. Komentarz XML dla cref do B:: test zostanie `<seealso cref="!:B::Test" />`, podczas gdy odwołanie do:: test jest poprawnie sformułowane `<seealso cref="M:A.Test" />`.

```cpp
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
