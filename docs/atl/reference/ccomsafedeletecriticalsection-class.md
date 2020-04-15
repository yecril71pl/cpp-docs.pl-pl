---
title: CComSafeDeleteKryrytycznaKlasa wysekcją
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: cb0dc440fc0e79e0023b5fbd6e4ca2345d031d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327367"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteKryrytycznaKlasa wysekcją

Ta klasa zawiera metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeDeleteKrytykaSekcja::CComSafeDeleteKryrytycznaSekcja](#ccomsafedeletecriticalsection)|Konstruktor.|
|[CComSafeDeleteKryrytycznasekcja::~CComSafeDeleteKryrytyscja](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeDeleteKrytykaSekcja::Init](#init)|Tworzy i inicjuje obiekt sekcji krytycznej.|
|[CComSafeDeleteKrytyka::Blokada](#lock)|Uzyskuje własność obiektu sekcji krytycznej.|
|[CComSafeDeleteKrytyka::Termin](#term)|Zwalnia zasoby systemowe używane przez obiekt sekcji krytycznej.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Oznacza, czy `CRITICAL_SECTION` obiekt wewnętrzny został zainicjowany.|

## <a name="remarks"></a>Uwagi

`CComSafeDeleteCriticalSection`pochodzi z klasy [CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md). Jednakże, `CComSafeDeleteCriticalSection` zapewnia dodatkowe mechanizmy bezpieczeństwa ponad [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Gdy wystąpienie `CComSafeDeleteCriticalSection` wykracza poza zakres lub jest jawnie usuwane z pamięci, podstawowy obiekt sekcji krytycznej zostanie automatycznie oczyszczony, jeśli jest nadal prawidłowy. Ponadto [CComSafeDeleteCriticalSection::Term](#term) metoda zakończy bezpiecznie, jeśli podstawowy obiekt sekcji krytycznej nie został jeszcze przydzielony lub został już zwolniony z pamięci.

Zobacz [CComCriticalSekcja, aby](../../atl/reference/ccomcriticalsection-class.md) uzyskać więcej informacji na temat krytycznych klas pomocnika sekcji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteKrytykaSekcja::CComSafeDeleteKryrytycznaSekcja

Konstruktor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Uwagi

Ustawia [element](#m_binitialized) członkowski m_bInitialized danych na FAŁSZ.

## <a name="ccomsafedeletecriticalsectionccomsafedeletecriticalsection"></a><a name="dtor"></a>CComSafeDeleteKryrytycznasekcja::~CComSafeDeleteKryrytyscja

Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia obiekt `CRITICAL_SECTION` wewnętrzny z pamięci, jeśli [m_bInitialized](#m_binitialized) element członkowski danych jest ustawiony na WARTOŚĆ TRUE.

## <a name="ccomsafedeletecriticalsectioninit"></a><a name="init"></a>CComSafeDeleteKrytykaSekcja::Init

Wywołuje implementację klasy podstawowej [Init](/visualstudio/debugger/init) i ustawia [m_bInitialized](#m_binitialized) na TRUE, jeśli się powiedzie.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik [CComCriticalSekcja::Init](../../atl/reference/ccomcriticalsection-class.md#init).

## <a name="ccomsafedeletecriticalsectionlock"></a><a name="lock"></a>CComSafeDeleteKrytyka::Blokada

Wywołuje implementację klasy podstawowej [Lock](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik [CComCriticalSekcja::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Uwagi

Ta metoda [zakłada,](#m_binitialized) że m_bInitialized element członkowski danych jest ustawiona na WARTOŚĆ PRAWDA po wprowadzeniu. Potwierdzenia jest generowany w debugowania kompilacji, jeśli ten warunek nie jest spełniony.

Aby uzyskać więcej informacji na temat zachowania funkcji, zobacz [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

## <a name="ccomsafedeletecriticalsectionm_binitialized"></a><a name="m_binitialized"></a>CComSafeDeleteKrytykaSekcja::m_bInitialized

Oznacza, czy `CRITICAL_SECTION` obiekt wewnętrzny został zainicjowany.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Uwagi

Element `m_bInitialized` członkowski danych służy do śledzenia `CRITICAL_SECTION` ważności obiektu źródłowego skojarzonego z klasą [CComSafeDeleteCriticalSection.](../../atl/reference/ccomsafedeletecriticalsection-class.md) `CRITICAL_SECTION` Podstawowy obiekt nie będzie próbował zostać zwolniony z pamięci, jeśli ta flaga nie jest ustawiona na WARTOŚĆ TRUE.

## <a name="ccomsafedeletecriticalsectionterm"></a><a name="term"></a>CComSafeDeleteKrytyka::Termin

Wywołuje implementację klasy podstawowej [CComCriticalSection::Term,](../../atl/reference/ccomcriticalsection-class.md#term) jeśli obiekt wewnętrzny `CRITICAL_SECTION` jest prawidłowy.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), lub S_OK, jeśli [m_bInitialized](#m_binitialized) został ustawiony na FAŁSZ przy wprowadzaniu.

### <a name="remarks"></a>Uwagi

Jest bezpieczne wywołanie tej metody, `CRITICAL_SECTION` nawet jeśli obiekt wewnętrzny jest nieprawidłowy. Destruktor tej klasy wywołuje tę metodę, jeśli element członkowski [m_bInitialized](#m_binitialized) danych jest ustawiony na WARTOŚĆ PRAWDA.

## <a name="see-also"></a>Zobacz też

[Klasa CComCriticalSekcja](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
