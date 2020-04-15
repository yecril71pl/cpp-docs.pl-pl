---
title: Klasa CSemaphore
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318497"
---
# <a name="csemaphore-class"></a>Klasa CSemaphore

Obiekt klasy `CSemaphore` reprezentuje "semafora" — obiekt synchronizacji, który umożliwia ograniczoną liczbę wątków w jednym lub więcej procesów, aby uzyskać dostęp do Utrzymuje liczbę wątków aktualnie uzyskujących dostęp do określonego zasobu.

## <a name="syntax"></a>Składnia

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Konstruuje `CSemaphore` obiekt.|

## <a name="remarks"></a>Uwagi

Semafory są przydatne w kontrolowaniu dostępu do zasobu udostępnionego, który może obsługiwać tylko ograniczoną liczbę użytkowników. Bieżąca liczba `CSemaphore` obiektu jest liczba dodatkowych użytkowników dozwolone. Gdy liczba osiągnie zero, wszystkie próby użycia zasobu kontrolowanego `CSemaphore` przez obiekt zostaną wstawione do kolejki systemowej i poczekaj, aż przekroczenie terminu lub liczba wzrośnie powyżej 0. Maksymalna liczba użytkowników, którzy mogą uzyskać dostęp do kontrolowanego `CSemaphore` zasobu w tym samym czasie jest określona podczas budowy obiektu.

Aby użyć `CSemaphore` obiektu, `CSemaphore` należy skonstruować obiekt, gdy jest to potrzebne. Określ nazwę semafora, na który chcesz czekać, i że aplikacja powinna początkowo być jej właścicielem. Następnie można uzyskać dostęp do semafora, gdy konstruktor zwraca. Wywołanie [CSyncObject::Odblokuj](../../mfc/reference/csyncobject-class.md#unlock) po zakończeniu uzyskiwania dostępu do kontrolowanego zasobu.

Alternatywną metodą `CSemaphore` używania obiektów jest `CSemaphore` dodanie zmiennej typu jako elementu członkowskiego danych do klasy, którą chcesz kontrolować. Podczas budowy kontrolowanego obiektu wywołać konstruktora elementu `CSemaphore` członkowskiego danych określając początkową liczbę dostępu, maksymalną liczbę dostępu, nazwę semafora (jeśli będzie używany przez granice procesu) i żądane atrybuty zabezpieczeń.

Aby uzyskać dostęp `CSemaphore` do zasobów kontrolowanych przez obiekty w ten sposób, najpierw należy utworzyć zmienną typu [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typu [CMultiLock](../../mfc/reference/cmultilock-class.md) w funkcji elementu członkowskiego dostępu zasobu. Następnie wywołaj funkcję `Lock` elementu członkowskiego obiektu blokady (na przykład [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). W tym momencie wątek będzie albo uzyskać dostęp do zasobu, czekać na zasób do zwolnienia i uzyskać dostęp lub czekać na zasób do zwolnienia i limit czasu, nie można uzyskać dostępu do zasobu. W każdym przypadku zasób został osiągnięty w sposób bezpieczny dla wątków. Aby zwolnić zasób, należy `Unlock` użyć funkcji elementu członkowskiego obiektu blokady (na przykład [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)) lub zezwolić obiektowi blokady na wypadnięcie poza zakres.

Alternatywnie można utworzyć `CSemaphore` obiekt autonomiczny i uzyskać do niego jawnie dostęp przed próbą uzyskania dostępu do kontrolowanego zasobu. Ta metoda, podczas gdy jaśniejsze dla osoby czytając kod źródłowy, jest bardziej podatne na błędy.

Aby uzyskać więcej informacji `CSemaphore` na temat używania obiektów, zobacz artykuł [Wielowątkowość: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject (100)](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore

Konstruuje obiekt o `CSemaphore` nazwie lub bez nazwy.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parametry

*lInitialCount*<br/>
Początkowa liczba użycia dla semafora. Musi być większa lub równa 0 i mniejsza lub równa *lMaxCount*.

*lMaxCount*<br/>
Maksymalna liczba użycia dla semafora. Musi być większa niż 0.

*pstrName (nazwa pstrname)*<br/>
Nazwa semafora. Musi być dostarczony, jeśli semafor będzie dostępny przez granice procesu. Jeśli `NULL`obiekt będzie bez nazwy. Jeśli nazwa pasuje do istniejącego semafora, konstruktor tworzy nowy `CSemaphore` obiekt, który odwołuje się do semafora tej nazwy. Jeśli nazwa pasuje do istniejącego obiektu synchronizacji, który nie jest semaforem, konstrukcja zakończy się niepowodzeniem.

*lpsaAttributes*<br/>
Atrybuty zabezpieczeń obiektu semafora. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) w windows SDK.

### <a name="remarks"></a>Uwagi

Aby uzyskać dostęp `CSemaphore` do obiektu lub zwolnić go, należy utworzyć obiekt [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) i wywołać jego funkcje elementów członkowskich [Lock](../../mfc/reference/csinglelock-class.md#lock) i [Unlock.](../../mfc/reference/csinglelock-class.md#unlock)

> [!IMPORTANT]
> Po utworzeniu `CSemaphore` obiektu należy użyć [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aby upewnić się, że obiekt mutex jeszcze nie istnieje. Jeśli mutex nie istnieje nieoczekiwanie, może to wskazywać, że proces nieuczciwych jest kucanie i może być zamierza użyć mutex złośliwie. W takim przypadku zalecana procedura dbająca o bezpieczeństwo jest zamknięcie dojścia i kontynuowanie tak, jakby wystąpił błąd w tworzeniu obiektu.

## <a name="see-also"></a>Zobacz też

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
