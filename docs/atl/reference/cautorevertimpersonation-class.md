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
ms.openlocfilehash: 799ec11fd8542a8b30ef3aa95f1a20700c5c9796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444918"
---
# <a name="cautorevertimpersonation-class"></a>Klasa CAutoRevertImpersonation

Ta klasa zostanie przywrócona [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektów nonimpersonating stanu, gdy jej wykracza poza zakres.

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
|[CAutoRevertImpersonation::Attach](#attach)|Automatyzuje operacja cofania personifikacji tokenu dostępu.|
|[CAutoRevertImpersonation::Detach](#detach)|Anuluje operacja cofania automatyczne personifikacji.|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|Pobiera bieżący token dostępu skojarzone z tym obiektem.|

## <a name="remarks"></a>Uwagi

[Token dostępu](/windows/desktop/SecAuthZ/access-tokens) jest obiektem, w tym artykule opisano proces lub wątek kontekstu zabezpieczeń, która jest przydzielona do każdego użytkownika zalogowanego systemu Windows NT lub Windows 2000. Te tokeny dostępu mogą być reprezentowane za pomocą `CAccessToken` klasy.

Czasami jest konieczne personifikacji tokenów dostępu. Ta klasa jest dostarczana jako udogodnienie, ale nie wykonuje personifikacji tokenów dostępu. wykonuje tylko automatyczna operacja cofania nonimpersonated stanu. Jest to spowodowane personifikacji tokenów dostępu mogą być wykonywane na kilka różnych sposobów.

Wprowadzenie do modelu kontroli dostępu w Windows, zobacz [kontroli dostępu](/windows/desktop/SecAuthZ/access-control) w zestawie Windows SDK.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsecurity.h

##  <a name="attach"></a>  CAutoRevertImpersonation::Attach

Automatyzuje operacja cofania personifikacji tokenu dostępu.

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*osobisty token dostępu*<br/>
Adres [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu, należy przywrócić automatycznie

### <a name="remarks"></a>Uwagi

Tej metody należy używać tylko, jeśli [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md) obiekt został utworzony przy użyciu wartości NULL `CAccessToken` wskaźnika, lub jeśli [Odłącz](#detach) został wcześniej wywołany. W prostych przypadkach nie jest konieczne użycie tej metody.

##  <a name="cautorevertimpersonation"></a>  CAutoRevertImpersonation::CAutoRevertImpersonation

Konstruuje `CAutoRevertImpersonation` obiektu.

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>Parametry

*osobisty token dostępu*<br/>
Adres [CAccessToken](../../atl/reference/caccesstoken-class.md) obiektu, należy przywrócić automatycznie.

### <a name="remarks"></a>Uwagi

Rzeczywiste personifikacji tokenu dostępu należy przeprowadzić oddzielnie z, a najlepiej przed tworzenie `CAutoRevertImpersonation` obiektu. Ten personifikację zostanie przywrócona automatycznie po `CAutoRevertImpersonation` obiekt wykracza poza zakres.

##  <a name="dtor"></a>  CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

Niszczy obiekt i przywraca personifikacji tokenu dostępu.

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Uwagi

Przywraca wszystkie personifikacji obecnie obowiązuje [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt udostępniany w konstrukcji lub za pomocą [Dołącz](#attach) metody. Jeśli nie `CAccessToken` jest związany, destruktor nie ma wpływu.

##  <a name="detach"></a>  CAutoRevertImpersonation::Detach

Anuluje operacja cofania automatyczne personifikacji.

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Adres wcześniej skojarzony [CAccessToken](../../atl/reference/caccesstoken-class.md), lub wartość NULL, jeśli istniały żadne skojarzenia.

### <a name="remarks"></a>Uwagi

Wywoływanie **Odłącz** zapobiega `CAutoRevertImpersonation` obiekt z Przywracanie wszelkich personifikacji obecnie obowiązuje [CAccessToken](../../atl/reference/caccesstoken-class.md) obiekt skojarzony z tym obiektem. `CAutoRevertImpersonation` następnie można zniszczeniu za pomocą żadnego efektu lub ponownie kojarzyć do tej samej lub innej `CAccessToken` przy użyciu [Dołącz](#attach).

##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken

Pobiera bieżący token dostępu skojarzone z tym obiektem.

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>Wartość zwracana

Adres wcześniej skojarzony [CAccessToken](../../atl/reference/caccesstoken-class.md), lub wartość NULL, jeśli istniały żadne skojarzenia.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda jest wywoływana dla celów, które zawierają operacja cofania personifikacji z `CAccessToken` obiektu [Odłącz](#detach) metoda powinna być używana zamiast tego.

## <a name="see-also"></a>Zobacz też

[Przykładowe ATLSecurity](../../visual-cpp-samples.md)<br/>
[Tokeny dostępu](/windows/desktop/SecAuthZ/access-tokens)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
