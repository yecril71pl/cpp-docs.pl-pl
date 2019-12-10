---
title: '> podsumowania &lt;C++ (Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 0620273f24573539897809b7892d46ad49b7aa57
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988586"
---
# <a name="ltsummarygt"></a>&gt; &lt;podsumowania

Aby opisać typ lub element członkowski typu, należy użyć tagu \<Summary >. Użyj [\<uwagi >](remarks-visual-cpp.md) , aby dodać informacje uzupełniające do opisu typu.

## <a name="syntax"></a>Składnia

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parametry

*zharmonizowan*<br/>
Podsumowanie obiektu.

## <a name="remarks"></a>Uwagi

Tekst dla tagu \<Summary > jest jedynym źródłem informacji o typie w technologii IntelliSense i jest również wyświetlany w [Przeglądarka obiektów](/visualstudio/ide/viewing-the-structure-of-code) i w raporcie w sieci Web komentarza do kodu.

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
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
