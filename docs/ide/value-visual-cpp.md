---
title: "&lt;wartość&gt; (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- value
- <value>
dev_langs: C++
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d1621a8251bddb1d4c7d1bf3f00c4ccf3ea5242
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltvaluegt-visual-c"></a>&lt;wartość&gt; (Visual C++)
\<Wartość > znacznik umożliwia opis właściwości i metod dostępu właściwości. Należy pamiętać, że podczas dodawania właściwości za pomocą Kreatora kodu w programie Visual Studio zintegrowane środowisko programistyczne, spowoduje to dodanie [ \<podsumowania >](../ide/summary-visual-cpp.md) tag nowej właściwości. Następnie należy ręcznie dodać \<wartość > tag do opisywania wartość, która reprezentuje właściwość.  
  
## <a name="syntax"></a>Składnia  
  
```  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Parametry  
 `property-description`  
 Opis właściwości.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluj z użyciem [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) na przetwarzanie komentarzy dokumentacji do pliku.  
  
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