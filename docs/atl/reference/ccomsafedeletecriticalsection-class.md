---
title: Klasa CComSafeDeleteCriticalSection
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
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821652"
---
# <a name="ccomsafedeletecriticalsection-class"></a>Klasa CComSafeDeleteCriticalSection

Ta klasa zapewnia metody uzyskiwania i zwalniania własności obiektu sekcji krytycznej.

## <a name="syntax"></a>Składnia

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|Konstruktor.|
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|Tworzy i inicjuje obiekt sekcji krytycznej.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Uzyskuje własność obiektu sekcji krytycznej.|
|[CComSafeDeleteCriticalSection::Term](#term)|Zwalnia zasoby systemowe używane przez obiekt sekcji krytycznej.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Określa, czy wewnętrzny obiekt `CRITICAL_SECTION` został zainicjowany.|

## <a name="remarks"></a>Uwagi

`CComSafeDeleteCriticalSection` pochodzi od klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Jednak `CComSafeDeleteCriticalSection` zapewnia dodatkowe mechanizmy bezpieczeństwa w porównaniu z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Gdy wystąpienie `CComSafeDeleteCriticalSection` wykracza poza zakres lub został jawnie usunięty z pamięci, podstawowy obiekt sekcji krytycznej zostanie automatycznie oczyszczony, jeśli jest nadal ważny. Ponadto Metoda [CComSafeDeleteCriticalSection:: Term](#term) zostanie bezpiecznie zakończona, jeśli podstawowy obiekt sekcji krytycznej nie został jeszcze przydzielony lub został już wystawiony z pamięci.

Aby uzyskać więcej informacji na temat krytycznych klas pomocników sekcji, zobacz [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore. h

##  <a name="ccomsafedeletecriticalsection"></a>CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Konstruktor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Uwagi

Ustawia element członkowski danych [m_bInitialized](#m_binitialized) na wartość false.

##  <a name="dtor"></a>  CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection

Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wewnętrzny obiekt `CRITICAL_SECTION` z pamięci, jeśli element członkowski danych [m_bInitialized](#m_binitialized) ma wartość true.

##  <a name="init"></a>CComSafeDeleteCriticalSection:: init

Wywołuje implementację klasy bazowej [init](/visualstudio/debugger/init) i ustawia [m_bInitialized](#m_binitialized) na true, jeśli powodzenie.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wynik elementu [CComCriticalSection:: init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

Wywołuje implementację klasy bazowej [blokady](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wynik elementu [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Uwagi

Ta metoda zakłada, że element członkowski danych [m_bInitialized](#m_binitialized) jest ustawiony na wartość true po wpisie. Potwierdzenie jest generowane w kompilacjach debugowania, jeśli ten warunek nie jest spełniony.

Aby uzyskać więcej informacji na temat zachowania funkcji, zobacz [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

Określa, czy wewnętrzny obiekt `CRITICAL_SECTION` został zainicjowany.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Uwagi

Element członkowski danych `m_bInitialized` służy do śledzenia ważności bazowego obiektu `CRITICAL_SECTION` skojarzonego z klasą [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) . Nie zostanie podjęta próba zwolnienia bazowego obiektu `CRITICAL_SECTION` z pamięci, jeśli ta flaga nie jest ustawiona na wartość TRUE.

##  <a name="term"></a>CComSafeDeleteCriticalSection:: Term

Wywołuje implementację klasy bazowej elementu [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term) , jeśli wewnętrzny obiekt `CRITICAL_SECTION` jest prawidłowy.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wynik [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)lub S_OK, jeśli [m_bInitialized](#m_binitialized) została ustawiona na wartość false przy wpisie.

### <a name="remarks"></a>Uwagi

Należy bezpiecznie wywołać tę metodę, nawet jeśli wewnętrzny obiekt `CRITICAL_SECTION` jest nieprawidłowy. Destruktor tej klasy wywołuje tę metodę, jeśli element członkowski danych [m_bInitialized](#m_binitialized) ma wartość true.

## <a name="see-also"></a>Zobacz także

[Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
