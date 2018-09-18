---
title: auto_gcroot, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: da63d58136d61bbea75daa90ac01cee5b44ac86d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039104"
---
# <a name="autogcroot-class"></a>auto_gcroot — Klasa
Zarządzanie zasobami automatyczne (takich jak [auto_ptr — klasa](../standard-library/auto-ptr-class.md)) który może służyć do osadzania wirtualnego dojścia do typu macierzystego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### <a name="parameters"></a>Parametry  
*_element_type*<br/>
Typ zarządzany, które można osadzać.  
  
## <a name="requirements"></a>Wymagania  
 **Plik nagłówkowy** \<msclr\auto_gcroot.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Zobacz też  
 [auto_gcroot —](../dotnet/auto-gcroot.md)   
 [auto_gcroot, składowe](../dotnet/auto-gcroot-members.md)   
 [Porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto_handle, klasa](../dotnet/auto-handle-class.md)