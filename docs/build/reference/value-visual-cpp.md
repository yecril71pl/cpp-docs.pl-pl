---
title: '> wartości &lt;(C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: de84d1faca59a6c8e4f82fba3605cbd54a05bd2e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988597"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

Tag \<wartość > umożliwia Opisanie metod metody dostępu właściwości i właściwości. Należy pamiętać, że po dodaniu właściwości z kreatorem kodu w zintegrowanym środowisku programistycznym programu Visual Studio zostanie dodany tag [\<summary >](summary-visual-cpp.md) dla nowej właściwości. Następnie należy ręcznie dodać tag \<wartość >, aby opisać wartość, którą reprezentuje właściwość.

## <a name="syntax"></a>Składnia

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parametry

*property-description*<br/>
Opis właściwości.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
