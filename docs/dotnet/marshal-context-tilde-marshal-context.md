---
title: 'marshal_context —:: ~ marshal_context — | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6cb7ed3c7b1ee5b28c4943d83b6a8ca6166b6d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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