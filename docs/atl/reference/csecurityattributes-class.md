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
ms.openlocfilehash: 66188a2c944379cfae813220937ac1e7e98fb41d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768344"
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

|Name|Opis|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|Wywołanie tej metody, aby ustawić atrybuty `CSecurityAttributes` obiektu.|

## <a name="remarks"></a>Uwagi

`SECURITY_ATTRIBUTES` Struktura zawiera [deskryptora zabezpieczeń](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) używane do tworzenia obiektu i określa, czy uchwyt pobierane przez określenie tej struktury jest dziedziczone.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

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

*rSecurityDescriptor*<br/>
Odwołanie do deskryptora zabezpieczeń.

*bInheritsHandle*<br/>
Określa, czy zwracany uchwyt jest dziedziczone, po utworzeniu nowego procesu. Jeśli ten element członkowski ma wartość true, nowy proces dziedziczy uchwytu.

##  <a name="set"></a>  CSecurityAttributes::Set

Wywołanie tej metody, aby ustawić atrybuty `CSecurityAttributes` obiektu.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Parametry

*rSecurityDescriptor*<br/>
Odwołanie do deskryptora zabezpieczeń.

*bInheritHandle*<br/>
Określa, czy zwracany uchwyt jest dziedziczone, po utworzeniu nowego procesu. Jeśli ten element członkowski ma wartość true, nowy proces dziedziczy uchwytu.

### <a name="remarks"></a>Uwagi

Ta metoda jest używana przez konstruktora, aby zainicjować `CSecurityAttributes` obiektu.

## <a name="see-also"></a>Zobacz także

[Zabezpieczenia — przykład](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)<br/>
[Deskryptor zabezpieczeń](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
