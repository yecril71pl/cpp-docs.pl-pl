---
title: '&lt;SeeAlso —&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <seealso>
- seealso
dev_langs:
- C++
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69cbf45ee37ff10f5b367bc3915647815b2ccd09
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376476"
---
# <a name="ltseealsogt-visual-c"></a>&lt;SeeAlso —&gt; (Visual C++)

\<SeeAlso — > należy określić tekst, który możesz chcieć pojawiają się w sekcji Zobacz też. Użyj [ \<zobacz >](../ide/see-visual-cpp.md) określić łącze między w tekście.

## <a name="syntax"></a>Składnia

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parametry

*Element członkowski*<br/>
Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

Kompilator sprawdza, czy dany element kodu istnieje i jest rozpoznawana jako `member` do nazwy elementu w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../ide/see-visual-cpp.md).

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

Zobacz [ \<podsumowania >](../ide/summary-visual-cpp.md) na przykład za pomocą \<SeeAlso — >.

Kompilator języka Visual C++ będzie próbował rozpoznać odwołania cref w jednym przebiegu za pomocą komentarzy dokumentacji.  W związku z tym, jeśli przy użyciu reguł wyszukiwania C++, symbolu nie można odnaleźć kompilatora odwołania zostaną oznaczone jako nierozwiązane.

## <a name="example"></a>Przykład

W poniższym przykładzie nierozpoznanych symboli jest przywoływany w cref. Komentarz XML dla cref do B::Test będzie `<seealso cref="!:B::Test" />`, odwołanie do A::Test jest poprawnie sformułowanym `<seealso cref="M:A.Test" />`.

```
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

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)