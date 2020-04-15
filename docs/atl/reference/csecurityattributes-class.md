---
title: Klasa CSecurityAttributes
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 113bcebb7461415590156206ee7aa4c91e0e93d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330986"
---
# <a name="csecurityattributes-class"></a>Klasa CSecurityAttributes

Ta klasa jest cienką otoką dla struktury atrybutów zabezpieczeń.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

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
|[CSecurityAttributes::Ustaw](#set)|Wywołanie tej metody, aby `CSecurityAttributes` ustawić atrybuty obiektu.|

## <a name="remarks"></a>Uwagi

Struktura `SECURITY_ATTRIBUTES` zawiera [deskryptor zabezpieczeń](/windows/win32/api/winnt/ns-winnt-security_descriptor) używany do tworzenia obiektu i określa, czy dojście pobrane przez określenie tej struktury jest dziedziczne.

Aby zapoznać się z wprowadzeniem do modelu kontroli dostępu w systemie Windows, zobacz [Kontrola dostępu](/windows/win32/SecAuthZ/access-control) w zestaw Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes

Konstruktor.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rDeptyptor zabezpieczeń*<br/>
Odwołanie do deskryptora zabezpieczeń.

*bInheritsHandle*<br/>
Określa, czy zwracany dojście jest dziedziczone podczas tworzenia nowego procesu. Jeśli ten element członkowski jest true, nowy proces dziedziczy dojście.

## <a name="csecurityattributesset"></a><a name="set"></a>CSecurityAttributes::Ustaw

Wywołanie tej metody, aby `CSecurityAttributes` ustawić atrybuty obiektu.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rDeptyptor zabezpieczeń*<br/>
Odwołanie do deskryptora zabezpieczeń.

*bInheritHandle (NieheritHandle)*<br/>
Określa, czy zwracany dojście jest dziedziczone podczas tworzenia nowego procesu. Jeśli ten element członkowski jest true, nowy proces dziedziczy dojście.

### <a name="remarks"></a>Uwagi

Ta metoda jest używana przez konstruktora do inicjowania `CSecurityAttributes` obiektu.

## <a name="see-also"></a>Zobacz też

[Przykład zabezpieczeń](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[deskryptor zabezpieczeń](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Globalne funkcje zabezpieczeń](../../atl/reference/security-global-functions.md)
