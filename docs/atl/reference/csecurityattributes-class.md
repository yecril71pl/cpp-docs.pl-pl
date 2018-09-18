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
ms.openlocfilehash: 672da1c98ebc51a7440e29234950be2adb5e1c0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093073"
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

## <a name="see-also"></a>Zobacz też

[Zabezpieczenia — przykład](../../visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)<br/>
[Deskryptor zabezpieczeń](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Funkcje globalne zabezpieczeń](../../atl/reference/security-global-functions.md)
