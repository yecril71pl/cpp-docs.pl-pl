---
title: Serializacja (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f4a410da74c37ee722c04f21e2cde906b9d061d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)