---
title: Klasa CAutoRevertImpersonation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
dev_langs:
- C++
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 942c446fc64bb7e4210bc82e21fc2511ae01503a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cautorevertimpersonation-class"></a>Klasa CAutoRevertImpersonation
Ta klasa umożliwia przywrócenie [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekty do nonimpersonating stanu, gdy przechodzi ona poza zakresem.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAutoRevertImpersonation
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Konstruuje `CAutoRevertImpersonation` obiektu|  
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|Niszczy obiekt i przywraca personifikacji tokenu dostępu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](#attach)|Automatyzuje odwrócenie personifikacji tokenu dostępu.|  
|[CAutoRevertImpersonation::Detach](#detach)|Anuluje odwrócenie automatycznej personifikacji.|  
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Pobiera bieżący token dostępu skojarzone z tym obiektem.|  
  
## <a name="remarks"></a>Uwagi  
 [Token dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909) jest obiekt, który opisuje kontekst zabezpieczeń proces lub Wątek i jest przydzielana każdy użytkownik zalogowany do systemu Windows NT lub Windows 2000. Może być reprezentowana te tokeny dostępu `CAccessToken` klasy.  
  
 Czasami zachodzi konieczność personifikacji tokenów dostępu. Ta klasa jest dostępny jako udogodnienie, ale nie przeprowadza personifikacji tokenów dostępu; przeprowadza tylko operacje automatyczne odwrócenie nonimpersonated stanu. Jest to spowodowane personifikacji tokenów dostępu mogą być wykonywane na kilka różnych sposobów.  
  
 Aby obejrzeć wprowadzenie do modelu kontroli dostępu w systemie Windows, temacie [kontroli dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374860) w zestawie Windows SDK.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsecurity.h  
  
##  <a name="attach"></a>  CAutoRevertImpersonation::Attach  
 Automatyzuje odwrócenie personifikacji tokenu dostępu.  
  
```
void Attach(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pAT`  
 Adres [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu przywrócenie automatycznie  
  
### <a name="remarks"></a>Uwagi  
 Tej metody należy używać tylko wtedy, gdy [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) obiekt został utworzony przy użyciu wartości NULL `CAccessToken` wskaźnika, lub jeśli [Detach](#detach) wywołano wcześniej. W przypadku prostego nie jest konieczne do używania tej metody.  
  
##  <a name="cautorevertimpersonation"></a>  CAutoRevertImpersonation::CAutoRevertImpersonation  
 Konstruuje `CAutoRevertImpersonation` obiektu.  
  
```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pAT`  
 Adres [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu przywrócenie automatycznie.  
  
### <a name="remarks"></a>Uwagi  
 Rzeczywiste personifikacji tokenu dostępu należy przeprowadzić oddzielnie od, najlepiej przed tworzeniem `CAutoRevertImpersonation` obiektu. Ta personifikacji zostaną cofnięte automatycznie po `CAutoRevertImpersonation` obiektu wykracza poza zakres.  
  
##  <a name="dtor"></a>  CAutoRevertImpersonation:: ~ CAutoRevertImpersonation  
 Niszczy obiekt i przywraca personifikacji tokenu dostępu.  
  
```
~CAutoRevertImpersonation() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Przywraca wszystkie personifikacji obecnie dotyczące [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu dostarczonego w konstrukcji lub za pomocą [Attach](#attach) metody. Jeśli nie `CAccessToken` jest skojarzony, destruktor nie ma wpływu.  
  
##  <a name="detach"></a>  CAutoRevertImpersonation::Detach  
 Anuluje odwrócenie automatycznej personifikacji.  
  
```
const CAccessToken* Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres wcześniej skojarzone [CAccessToken](../../atl/reference/caccesstoken-class.md), lub wartość NULL, jeśli istniały żadne skojarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywoływanie **Detach** uniemożliwia `CAutoRevertImpersonation` Przywracanie wszelkich personifikacji obecnie dla obiekt [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt skojarzony z tym obiektem. `CAutoRevertImpersonation` następnie można zniszczone bez zmiany lub ponownie kojarzyć na tym samym lub innym `CAccessToken` przy użyciu [Attach](#attach).  
  
##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken  
 Pobiera bieżący token dostępu skojarzone z tym obiektem.  
  
```
const CAccessToken* GetAccessToken() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres wcześniej skojarzone [CAccessToken](../../atl/reference/caccesstoken-class.md), lub wartość NULL, jeśli istniały żadne skojarzenia.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda jest wywoływana dla celów, które obejmują odwrócenie personifikacji z `CAccessToken` obiektu [Detach](#detach) metody należy użyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ATLSecurity](../../visual-cpp-samples.md)   
 [Tokeny dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Przegląd klas](../../atl/atl-class-overview.md)
