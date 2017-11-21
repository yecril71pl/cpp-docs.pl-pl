---
title: Klasa CSecurityAttributes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs: C++
helpviewer_keywords: CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8ed8a9336a60b3577f856f0bc2bd6baa358aec6d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csecurityattributes-class"></a>Klasa CSecurityAttributes
Ta klasa jest cienką otoką dla struktury atrybutów zabezpieczeń.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSecurityAttributes::Set](#set)|Wywołanie tej metody, aby ustawić atrybuty `CSecurityAttributes` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 **SECURITY_ATTRIBUTES** struktura zawiera [deskryptora zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379561) używany do tworzenia obiektu i określa, czy dziedziczne dojście pobierane przez określenie tej struktury.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes  
 Konstruktor.  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSecurityDescriptor`  
 Odwołanie do deskryptora zabezpieczeń.  
  
 `bInheritsHandle`  
 Określa, czy zwrócone dojścia jest dziedziczone po utworzeniu nowego procesu. Jeśli ten element członkowski ma wartość true, nowy proces dziedziczy dojście.  
  
##  <a name="set"></a>CSecurityAttributes::Set  
 Wywołanie tej metody, aby ustawić atrybuty `CSecurityAttributes` obiektu.  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `rSecurityDescriptor`  
 Odwołanie do deskryptora zabezpieczeń.  
  
 `bInheritHandle`  
 Określa, czy zwrócone dojścia jest dziedziczone po utworzeniu nowego procesu. Jeśli ten element członkowski ma wartość true, nowy proces dziedziczy dojście.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używana przez konstruktora zainicjować `CSecurityAttributes` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [Deskryptor zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
