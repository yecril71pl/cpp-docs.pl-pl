---
title: auto_gcroot — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
dev_langs:
- C++
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b6afad3450aff2a9243b3e4a480a374fbcd14fc7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103869"
---
# <a name="autogcroot-class"></a>auto_gcroot — Klasa
Zarządzanie zasobami automatyczne (takich jak [auto_ptr — klasa](../standard-library/auto-ptr-class.md)) które mogą służyć do osadzenia wirtualnego dojścia do typu macierzystego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>Parametry  
 `_element_type`  
 Typ zarządzany do osadzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówka** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [auto_gcroot —](../dotnet/auto-gcroot.md)   
 [auto_gcroot — członkowie](../dotnet/auto-gcroot-members.md)   
 [Porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle, klasa](../dotnet/auto-handle-class.md)