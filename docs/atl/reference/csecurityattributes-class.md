---
title: Klasa CSecurityAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
dev_langs:
- C++
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc37dd8025009e4f904373fc8aa106c93dc8210
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879350"
---
# <a name="csecurityattributes-class"></a>Klasa CSecurityAttributes
Ta klasa jest otoką alokowania elastycznego w strukturze atrybuty zabezpieczeń.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
 `SECURITY_ATTRIBUTES` Struktura zawiera [deskryptora zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379561) używane do tworzenia obiektu i określa, czy uchwyt pobierane przez określenie tej struktury jest dziedziczone.  
  
 Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `SECURITY_ATTRIBUTES`  
  
 `CSecurityAttributes`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes  
 Konstruktor.  
  
```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *rSecurityDescriptor*  
 Odwołanie do deskryptora zabezpieczeń.  
  
 *bInheritsHandle*  
 Określa, czy zwracany uchwyt jest dziedziczone, po utworzeniu nowego procesu. Jeśli ten element członkowski ma wartość true, nowy proces dziedziczy uchwytu.  
  
##  <a name="set"></a>  CSecurityAttributes::Set  
 Wywołanie tej metody, aby ustawić atrybuty `CSecurityAttributes` obiektu.  
  
```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *rSecurityDescriptor*  
 Odwołanie do deskryptora zabezpieczeń.  
  
 *bInheritHandle*  
 Określa, czy zwracany uchwyt jest dziedziczone, po utworzeniu nowego procesu. Jeśli ten element członkowski ma wartość true, nowy proces dziedziczy uchwytu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest używana przez konstruktora, aby zainicjować `CSecurityAttributes` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia — przykład](../../visual-cpp-samples.md)   
 [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)   
 [Deskryptor zabezpieczeń](http://msdn.microsoft.com/library/windows/desktop/aa379561)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
