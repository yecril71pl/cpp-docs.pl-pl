---
title: Klasa CMutex
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363284"
---
# <a name="cmutex-class"></a>Klasa CMutex

Reprezentuje "mutex" — obiekt synchronizacji, który umożliwia jeden wątek wzajemnie wykluczające się dostęp do zasobu.

## <a name="syntax"></a>Składnia

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Konstruuje `CMutex` obiekt.|

## <a name="remarks"></a>Uwagi

Muteksy są przydatne, gdy tylko jeden wątek naraz może być dozwolony do modyfikowania danych lub innego kontrolowanego zasobu. Na przykład dodawanie węzłów do połączonej listy jest procesem, który powinien być dozwolony tylko przez jeden wątek naraz. Za pomocą `CMutex` obiektu do kontrolowania połączonej listy, tylko jeden wątek naraz może uzyskać dostęp do listy.

Aby użyć `CMutex` obiektu, `CMutex` należy skonstruować obiekt, gdy jest to potrzebne. Określ nazwę obiektu mutex, na którym chcesz czekać, i że aplikacja powinna początkowo być jej właścicielem. Następnie można uzyskać dostęp do obiektu mutex, gdy konstruktor zwraca. Wywołanie [CSyncObject::Odblokuj](../../mfc/reference/csyncobject-class.md#unlock) po zakończeniu uzyskiwania dostępu do kontrolowanego zasobu.

Alternatywną metodą `CMutex` używania obiektów jest `CMutex` dodanie zmiennej typu jako elementu członkowskiego danych do klasy, którą chcesz kontrolować. Podczas budowy kontrolowanego obiektu wywołać konstruktora elementu członkowskiego `CMutex` danych określając, czy obiekt mutex jest początkowo własnością, nazwę obiektu mutex (jeśli będzie używany przez granice procesu) i żądane atrybuty zabezpieczeń.

Aby uzyskać dostęp `CMutex` do zasobów kontrolowanych przez obiekty w ten sposób, najpierw należy utworzyć zmienną typu [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typu [CMultiLock](../../mfc/reference/cmultilock-class.md) w funkcji elementu członkowskiego dostępu zasobu. Następnie wywołaj funkcję `Lock` elementu członkowskiego obiektu blokady (na przykład [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). W tym momencie wątek będzie albo uzyskać dostęp do zasobu, czekać na zasób do zwolnienia i uzyskać dostęp lub czekać na zasób do zwolnienia i limit czasu, nie można uzyskać dostępu do zasobu. W każdym przypadku zasób został osiągnięty w sposób bezpieczny dla wątków. Aby zwolnić zasób, należy `Unlock` użyć funkcji elementu członkowskiego obiektu blokady (na przykład [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)) lub zezwolić obiektowi blokady na wypadnięcie poza zakres.

Aby uzyskać więcej `CMutex` informacji na temat używania obiektów, zobacz artykuł [Wielowątkowość: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject (100)](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex

Konstruuje obiekt o `CMutex` nazwie lub bez nazwy.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bNienajleszaninowo*<br/>
Określa, czy wątek `CMutex` tworzący obiekt początkowo ma dostęp do zasobu kontrolowanego przez obiekt mutex.

*Lpszname*<br/>
Nazwa `CMutex` obiektu. Jeśli istnieje inny obiekt mutex o tej samej nazwie, należy podać *lpszName,* jeśli obiekt będzie używany przez granice procesu. Jeśli **NULL**, mutex będzie bez nazwy. Jeśli nazwa pasuje do istniejącego obiektu mutex, `CMutex` konstruktor tworzy nowy obiekt, który odwołuje się do obiektu o tej nazwie. Jeśli nazwa pasuje do istniejącego obiektu synchronizacji, który nie jest obiektem mutex, konstrukcja zakończy się niepowodzeniem.

*lpsaAttribute*<br/>
Atrybuty zabezpieczeń obiektu mutex. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) w windows SDK.

### <a name="remarks"></a>Uwagi

Aby uzyskać dostęp `CMutex` do obiektu lub zwolnić go, należy utworzyć obiekt [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) i wywołać jego funkcje elementów członkowskich [Lock](../../mfc/reference/csinglelock-class.md#lock) i [Unlock.](../../mfc/reference/csinglelock-class.md#unlock) Jeśli `CMutex` obiekt jest używany autonomiczny, `Unlock` wywołać jego funkcji elementu członkowskiego, aby go zwolnić.

> [!IMPORTANT]
> Po utworzeniu `CMutex` obiektu należy użyć [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aby upewnić się, że obiekt mutex jeszcze nie istnieje. Jeśli mutex nie istnieje nieoczekiwanie, może to wskazywać, że proces nieuczciwych jest kucanie i może być zamierza użyć mutex złośliwie. W takim przypadku zalecana procedura dbająca o bezpieczeństwo jest zamknięcie dojścia i kontynuowanie tak, jakby wystąpił błąd w tworzeniu obiektu.

## <a name="see-also"></a>Zobacz też

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
