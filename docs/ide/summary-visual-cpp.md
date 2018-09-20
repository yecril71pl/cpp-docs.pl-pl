---
title: '&lt;Podsumowanie&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <summary>
- summary
dev_langs:
- C++
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1a81bc910ca9d1682fa5093b4d3027b8090f585
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397354"
---
# <a name="ltsummarygt-visual-c"></a>&lt;Podsumowanie&gt; (Visual C++)

\<Podsumowania > tag powinien być używany do opisu typu lub składowej typu. Użyj [ \<Uwagi >](../ide/remarks-visual-cpp.md) można dodać dodatkowe informacje do opisu typu.

## <a name="syntax"></a>Składnia

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parametry

*Opis elementu*<br/>
Podsumowanie obiektu.

## <a name="remarks"></a>Uwagi

Tekst dla \<podsumowania > tag to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany na [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) i w raporcie Web komentarzy kodu.

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)