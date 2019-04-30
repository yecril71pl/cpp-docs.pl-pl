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
ms.openlocfilehash: 794a71ae9a146b691ba6a4377a7fdf2c3ddd3501
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384676"
---
# <a name="serialization-ccli"></a>Serializacja (C++/CLI)

Serializacja (proces przechowywania stanu obiektu lub elementu członkowskiego na stałe średni) klas zarządzanych (w tym poszczególne pola lub właściwości) jest obsługiwana przez <xref:System.SerializableAttribute> i <xref:System.NonSerializedAttribute> klasy.

## <a name="remarks"></a>Uwagi

Zastosuj **SerializableAttribute** atrybut niestandardowy do zarządzanej klasy do serializacji całej klasy lub zastosować tylko do określonych pól lub właściwości, aby serializować części klasy zarządzanej. Użyj **NonSerializedAttribute** niestandardowego atrybutu w celu zwolnienia pól lub właściwości klasy zarządzanej z serializacji.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

W poniższym przykładzie klasa `MyClass` (i właściwość `m_nCount`) jest oznaczony jako możliwy do serializacji. Jednak `m_nData` właściwość nie jest serializowana, wskazane przez **NonSerialized** atrybutów niestandardowych:

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

Należy pamiętać, że oba atrybuty można odwoływać się za pomocą "krótkiej nazwy" (**Serializable** i **NonSerialized**). Dodatkowo jest to wyjaśnione w [stosowanie atrybutów](/dotnet/standard/attributes/applying-attributes).

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
