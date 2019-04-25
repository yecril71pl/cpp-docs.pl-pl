---
title: CComSafeDeleteCriticalSection Class
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
ms.openlocfilehash: 0269079db97e2ff91767c9c0c74a9336fce81ade
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258887"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection Class

Ta klasa dostarcza metody do uzyskania i zwalniania własności obiektu sekcję krytyczną.

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
|[CComSafeDeleteCriticalSection::Init](#init)|Tworzy i inicjuje obiekt sekcję krytyczną.|
|[CComSafeDeleteCriticalSection::Lock](#lock)|Uzyskuje własność obiektu sekcję krytyczną.|
|[CComSafeDeleteCriticalSection::Term](#term)|Zwalnia zasoby systemowe używane przez obiekt sekcję krytyczną.|

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_bInitialized](#m_binitialized)|Flagi czy wewnętrzny `CRITICAL_SECTION` obiekt został zainicjowany.|

## <a name="remarks"></a>Uwagi

`CComSafeDeleteCriticalSection` pochodzi z klasy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md). Jednak `CComSafeDeleteCriticalSection` udostępnia mechanizmy dodatkowego bezpieczeństwa w porównaniu z [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).

Jeśli wystąpienie `CComSafeDeleteCriticalSection` wykracza poza zakres lub jest jawnie usunięte z pamięci, obiekt źródłowy sekcję krytyczną zostaną automatycznie wyczyszczone, jeśli jest nadal ważny. Ponadto [CComSafeDeleteCriticalSection::Term](#term) metoda zostanie zakończona bez problemu zmieniała, jeśli obiekt źródłowy sekcję krytyczną nie został jeszcze przydzielony lub zostało już zwolnione z pamięci.

Zobacz [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) więcej informacji na temat klas pomocniczych sekcję krytyczną.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

Konstruktor.

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Uwagi

Zestawy [m_bInitialized](#m_binitialized) element członkowski danych na wartość FALSE.

##  <a name="dtor"></a>  CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection

Destruktor.

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wewnętrzny `CRITICAL_SECTION` obiekt z pamięci, jeśli [m_bInitialized](#m_binitialized) element członkowski danych jest ustawiona na wartość TRUE.

##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init

Wywołania implementacji klasy podstawowej [Init](/visualstudio/debugger/init) i ustawia [m_bInitialized](#m_binitialized) na wartość TRUE, jeśli to się powiedzie.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik [CComCriticalSection::Init](../../atl/reference/ccomcriticalsection-class.md#init).

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

Wywołania implementacji klasy podstawowej [blokady](ccomcriticalsection-class.md#lock).

```
HRESULT Lock();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

### <a name="remarks"></a>Uwagi

Ta metoda przyjmuje [m_bInitialized](#m_binitialized) element członkowski danych jest ustawiona na wartość TRUE po wejściu. Potwierdzenie jest generowany w kompilacjach debugowania, gdy ten condidtion nie jest spełniony.

Aby uzyskać więcej informacji na temat zachowania funkcji, zobacz [CComCriticalSection::Lock](../../atl/reference/ccomcriticalsection-class.md#lock).

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

Flagi czy wewnętrzny `CRITICAL_SECTION` obiekt został zainicjowany.

```
bool m_bInitialized;
```

### <a name="remarks"></a>Uwagi

`m_bInitialized` Element członkowski danych jest używane do śledzenia ważności podstawowych `CRITICAL_SECTION` obiekt skojarzony z [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) klasy. Podstawowe `CRITICAL_SECTION` obiekt nie zostanie podjęta próba zwolniona z pamięci, jeśli ta flaga nie jest ustawiona na wartość TRUE.

##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term

Wywołania implementacji klasy podstawowej [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term) jeśli wewnętrzny `CRITICAL_SECTION` obiekt jest prawidłowy.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wynik [CComCriticalSection::Term](../../atl/reference/ccomcriticalsection-class.md#term), lub S_OK Jeśli [m_bInitialized](#m_binitialized) została ustawiona na FALSE, po wejściu.

### <a name="remarks"></a>Uwagi

Można bezpiecznie wywołać tej metody, nawet jeśli wewnętrzny `CRITICAL_SECTION` obiektu jest nieprawidłowy. Destruktor tej klasy wywołuje tę metodę, jeśli [m_bInitialized](#m_binitialized) element członkowski danych jest ustawiona na wartość TRUE.

## <a name="see-also"></a>Zobacz także

[Klasa CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
