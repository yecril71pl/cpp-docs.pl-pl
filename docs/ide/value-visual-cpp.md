---
title: '&lt;wartość&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- value
- <value>
dev_langs:
- C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a194e45fd79ae59dc91abb21a9fb038d3ec4008
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041691"
---
# <a name="ltvaluegt-visual-c"></a>&lt;wartość&gt; (Visual C++)
\<Wartość > znacznik umożliwia opisują właściwości i metod dostępu właściwości. Należy pamiętać, że po dodaniu właściwości za pomocą Kreatora kodu w programie Visual Studio zintegrowanego środowiska programistycznego, spowoduje to dodanie [ \<podsumowania >](../ide/summary-visual-cpp.md) tag w przypadku nowej właściwości. Następnie należy ręcznie dodać \<wartość > tag do opisania wartość, która reprezentuje właściwość.  
  
## <a name="syntax"></a>Składnia  
  
```  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
*Opis właściwości*<br/>
Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)