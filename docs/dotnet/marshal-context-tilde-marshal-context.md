---
title: "marshal_context —:: ~ marshal_context — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs: C++
helpviewer_keywords: marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 42af11d58804a000e630d916cd5887c5005aa955
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context
Niszczy `marshal_context` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
~marshal_context();  
```  
  
## <a name="remarks"></a>Uwagi  
 Konwersje niektórych danych wymaga kontekstu kierowanie. Zobacz [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji na temat tłumaczenia, które wymagają kontekst i który zawiera plik musi zostać uwzględniony w aplikacji.  
  
 Usuwanie `marshal_context` obiektu unieważni dane przekonwertować w tym kontekście. Jeśli chcesz zachować dane po `marshal_context` obiektu, należy ręcznie skopiować dane do zmiennej zostanie utrzymana.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as —](../dotnet/marshal-as.md)   
 [marshal_context, klasa](../dotnet/marshal-context-class.md)