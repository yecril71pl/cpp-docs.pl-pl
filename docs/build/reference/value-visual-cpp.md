---
title: '&lt;wartość > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: c0863b41791254992d16d373328ff6c8a5d6f94f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317032"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

\<Wartość > znacznik umożliwia opisują właściwości i metod dostępu właściwości. Należy pamiętać, że po dodaniu właściwości za pomocą Kreatora kodu w programie Visual Studio zintegrowanego środowiska programistycznego, spowoduje to dodanie [ \<podsumowania >](summary-visual-cpp.md) tag w przypadku nowej właściwości. Następnie należy ręcznie dodać \<wartość > tag do opisania wartość, która reprezentuje właściwość.

## <a name="syntax"></a>Składnia

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parametry

*property-description*<br/>
Opis właściwości.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```
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
