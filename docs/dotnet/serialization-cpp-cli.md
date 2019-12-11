---
title: Serializacja (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: b2dfdcaf1a1f33e89d106d4529ffc9af2d08376b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988407"
---
# <a name="serialization-ccli"></a>Serializacja (C++/CLI)

Serializacja (proces przechowywania stanu obiektu lub elementu członkowskiego na stałe medium) zarządzanych klas (w tym poszczególnych pól lub właściwości) jest obsługiwana przez klasy <xref:System.SerializableAttribute> i <xref:System.NonSerializedAttribute>.

## <a name="remarks"></a>Uwagi

Zastosuj atrybut niestandardowy **SerializableAttribute** do zarządzanej klasy, aby serializować całą klasę lub zastosować tylko do określonych pól lub właściwości do serializacji części klasy zarządzanej. Użyj **Nieserializowanego** atrybutu niestandardowegoattribute do wykluczenia pól lub właściwości klasy zarządzanej z serializowania.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie Klasa `MyClass` (i Właściwość `m_nCount`) jest oznaczona jako możliwy do serializacji. Jednak Właściwość `m_nData` nie jest serializowana zgodnie z oznaczeniem **Nieserializowanego** atrybutu niestandardowego:

### <a name="code"></a>Kod

```cpp
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

Należy pamiętać, że obydwa atrybuty mogą być przywoływane przy użyciu "krótkiej nazwy" (**serializować** i **nieszeregowane**). Jest to dokładniej wyjaśnione w temacie [stosowanie atrybutów](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
