---
title: '&lt;Podsumowanie > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 68bb8b7c269b3406438e5cf21dde7179f7e67646
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823287"
---
# <a name="ltsummarygt"></a>&lt;Podsumowanie&gt;

\<Podsumowania > tag powinien być używany do opisu typu lub składowej typu. Użyj [ \<Uwagi >](remarks-visual-cpp.md) można dodać dodatkowe informacje do opisu typu.

## <a name="syntax"></a>Składnia

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Podsumowanie obiektu.

## <a name="remarks"></a>Uwagi

Tekst dla \<podsumowania > tag to jedyne źródło informacji o typie w technologii IntelliSense i jest wyświetlany na [przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code) i w raporcie Web komentarzy kodu.

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

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

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)