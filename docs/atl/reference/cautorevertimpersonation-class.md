---
title: Klasa CAutoRevertImpersonation
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: ea119436fd36d0814c05f1b48380028ad3f63f0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748239"
---
# <a name="cautorevertimpersonation-class"></a>Klasa CAutoRevertImpersonation

Ta klasa przywraca [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektów do stanu nieimipersonalnej, gdy wychodzi poza zakres.

## <a name="syntax"></a>Składnia

```
class CAutoRevertImpersonation
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|Konstruuje `CAutoRevertImpersonation` obiekt|
|[CAutoRevertImpersonation::~CAutoRevertImpersonation](#dtor)|Niszczy obiekt i przywraca personifikacji tokenu dostępu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAutoRevertImpersonation::Dołącz](#attach)|Automatyzuje ponowne personifikacji tokenu dostępu.|
|[CAutoRevertImpersonation::Detach](#detach)|Anuluje automatyczną konwersję personifikacji.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Pobiera bieżący token dostępu skojarzony z tym obiektem.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/win32/SecAuthZ/access-tokens) jest obiektem opisującym kontekst zabezpieczeń procesu lub wątku i przydzielanym każdemu użytkownikowi zalogowanym do systemu Windows NT lub Windows 2000. Te tokeny dostępu mogą być `CAccessToken` reprezentowane z klasy.

Czasami konieczne jest personifikacji tokenów dostępu. Ta klasa jest dostarczana jako wygoda, ale nie wykonuje personifikacji tokenów dostępu; wykonuje tylko automatyczne ponowne odwrotowanie do stanu nieispersonatycznego. Jest tak, ponieważ personifikacji dostępu do tokenu można wykonać na kilka różnych sposobów.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>CAutoRevertImpersonation::Dołącz

Automatyzuje ponowne personifikacji tokenu dostępu.

```cpp
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*Pat*<br/>
Adres obiektu [CAccessToken,](../../atl/reference/caccesstoken-class.md) który ma zostać automatycznie przywrócony

### <a name="remarks"></a>Uwagi

Ta metoda powinna być używana tylko wtedy, gdy [obiekt CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) został utworzony za pomocą wskaźnika NULL `CAccessToken` lub jeśli [Detach](#detach) został wywołany wcześniej. W prostych przypadkach nie jest konieczne użycie tej metody.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

Konstruuje `CAutoRevertImpersonation` obiekt.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*Pat*<br/>
Adres [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu do odwołania automatycznie.

### <a name="remarks"></a>Uwagi

Rzeczywiste personifikacji tokenu dostępu powinny być wykonywane oddzielnie od `CAutoRevertImpersonation` i najlepiej przed utworzeniem obiektu. Ta personifikacja zostanie przywrócona automatycznie, `CAutoRevertImpersonation` gdy obiekt wyjdzie poza zakres.

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>CAutoRevertImpersonation::~CAutoRevertImpersonation

Niszczy obiekt i przywraca personifikacji tokenu dostępu.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Uwagi

Przywraca wszelkie personifikacji obecnie obowiązujące dla [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu pod warunkiem, na budowie lub za pośrednictwem [Attach](#attach) metody. Jeśli `CAccessToken` nie jest skojarzony, destruktor nie ma wpływu.

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>CAutoRevertImpersonation::Detach

Anuluje automatyczną konwersję personifikacji.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Adres wcześniej skojarzonego [CAccessToken](../../atl/reference/caccesstoken-class.md)lub NULL, jeśli nie istniało żadne skojarzenie.

### <a name="remarks"></a>Uwagi

Wywołanie **Detach** `CAutoRevertImpersonation` uniemożliwia obiektowi ponowne cofnięcie wszelkich personifikacji aktualnie obowiązujących dla [obiektu CAccessToken](../../atl/reference/caccesstoken-class.md) skojarzonego z tym obiektem. `CAutoRevertImpersonation`można następnie zniszczyć bez efektu lub ponownie szesnasty z tym samym lub innym `CAccessToken` obiektem za pomocą [Dołącz](#attach).

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>CAutoRevertImpersonation::GetAccessToken

Pobiera bieżący token dostępu skojarzony z tym obiektem.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Wartość zwracana

Adres wcześniej skojarzonego [CAccessToken](../../atl/reference/caccesstoken-class.md)lub NULL, jeśli nie istniało żadne skojarzenie.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda jest wywoływana do celów, które obejmują `CAccessToken` odwrócenie personifikacji obiektu, Zamiast tego należy użyć [Metody Detach.](#detach)

## <a name="see-also"></a>Zobacz też

[Przykład ATLSecurity](../../overview/visual-cpp-samples.md)<br/>
[Tokeny dostępu](/windows/win32/SecAuthZ/access-tokens)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
