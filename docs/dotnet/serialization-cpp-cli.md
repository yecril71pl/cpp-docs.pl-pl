---
title: Serializacja (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57ec673e945d0db14ce8fee0d477d7aeb2a9e238
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="serialization-ccli"></a>Serializacja (C++/CLI)
Serializacja (proces przechowywania stanu obiektu lub elementu członkowskiego, stałego średni) klas zarządzanych (w tym poszczególnych pól lub właściwości) jest obsługiwana przez <xref:System.SerializableAttribute> i <xref:System.NonSerializedAttribute> klasy.  
  
## <a name="remarks"></a>Uwagi  
 Zastosuj **SerializableAttribute** atrybutu niestandardowego do zarządzanej klasy do serializacji całej klasy lub zastosować tylko do określonych pól lub właściwości do serializacji części zarządzanej klasy. Użyj **NonSerializedAttribute** atrybutu niestandardowego wykluczone pola lub właściwości zarządzanej klasy z serializowana.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie klasa `MyClass` (i właściwości `m_nCount`) jest oznaczony jako możliwy do serializacji. Jednak `m_nData` wskazywany przez właściwość nie jest serializowany **NonSerialized** atrybutu niestandardowego:  
  
### <a name="code"></a>Kod  
  
```  
// serialization_and_mcpp.cpp  
// compile with: /LD /clr  
using namespace System;  
  
[ Serializable ]  
public ref class MyClass {  
public:  
   int m_nCount;  
private:  
   [ NonSerialized ]  
   int m_nData;  
};  
```  
  
### <a name="comments"></a>Komentarze  
 Należy pamiętać, że oba atrybuty można odwoływać się przy użyciu ich "krótkiej nazwy" (**Serializable** i **NonSerialized**). To jest omówiona w [stosowanie atrybutów](/dotnet/standard/attributes/applying-attributes).  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)