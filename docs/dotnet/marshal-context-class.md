---
title: marshal_context — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6bf712e960cbf96ccef6c3a3e4efebdad9045818
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136997"
---
# <a name="marshalcontext-class"></a>marshal_context — Klasa
Ta klasa konwertuje dane między środowiskach natywnych i zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class marshal_context  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj `marshal_context` klasy dla konwersji danych, które wymagają kontekstu. Zobacz [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md) uzyskać więcej informacji o konwersji, które wymagają kontekstu i organizowania plik, który ma zostać uwzględniony. Wynik przekazywanie, korzystając z kontekstu jest prawidłowy tylko do `marshal_context` obiekt zostanie zniszczony. Aby zachować wyników, należy skopiować dane.  
  
 Taki sam `marshal_context` może służyć do wielu konwersji danych. Ponowne wykorzystywanie kontekstu w ten sposób nie wpłynie na wyników z poprzedniego wywołania kierowania.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, lub \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)