---
title: marshal_context::marshal_context | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1e8838864c4ec1c6414401608b848cb12b01c16e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33140123"
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context
Konstruuje `marshal_context` obiektu do użycia dla danych Konwersja typów danych zarządzanego i natywnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
marshal_context();  
```  
  
## <a name="remarks"></a>Uwagi  
 Konwersje niektórych danych wymaga kontekstu kierowanie. Zobacz [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji na temat tłumaczenia, które wymagają kontekst i który zawiera plik musi zostać uwzględniony w aplikacji.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as —](../dotnet/marshal-as.md)   
 [marshal_context, klasa](../dotnet/marshal-context-class.md)