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
ms.openlocfilehash: f85e562af9d048503be20d1ab5d219fe8d2d039f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373651"
---
# <a name="cmutex-class"></a>Klasa CMutex

Reprezentuje "mutex" — obiekt synchronizacji, który umożliwia jeden wątek wzajemnie wykluczających się uzyskanie dostępu do zasobu.

## <a name="syntax"></a>Składnia

```
class CMutex : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMutex::CMutex](#cmutex)|Konstruuje `CMutex` obiektu.|

## <a name="remarks"></a>Uwagi

Muteksy są przydatne, gdy tylko jeden wątek jednocześnie można zezwolić na modyfikowanie danych lub innego zasobu kontrolowany. Na przykład dodawanie węzłów do połączonej listy jest procesem, który powinien być dozwolony tylko przez jeden wątek jednocześnie. Za pomocą `CMutex` obiektu do kontrolowania liście połączonej, tylko jeden wątek jednocześnie uzyskać dostęp do listy.

Aby użyć `CMutex` obiektów, konstruowania `CMutex` obiektu, kiedy jest to konieczne. Określ nazwę chcesz czekać na element mutex, a aplikacja początkowo powinny odpowiadać. Gdy Konstruktor zwraca access element mutex. Wywołaj [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po zakończeniu dostęp do zasobu kontrolowany.

Alternatywna metoda przy użyciu `CMutex` obiektów jest dodanie do zmiennej typu `CMutex` jako element członkowski danych do klasy, do kontroli. Podczas konstruowania obiektu kontrolowanego, należy wywołać konstruktora `CMutex` określenie, jeśli element mutex początkowo jest właścicielem, nazwa obiektu mutex (Jeśli zostanie on użyty przez granice procesu) i żądane atrybuty zabezpieczeń element członkowski danych.

Dostęp do zasobów w wartości clientauthtrustmode `CMutex` obiektów w ten sposób, najpierw Utwórz zmienną typu albo [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typ [CMultiLock](../../mfc/reference/cmultilock-class.md) w funkcji składowej dostępu do zasobu. Następnie wywołaj zablokować obiektu `Lock` funkcja elementu członkowskiego (na przykład [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). W tym momencie wątek będzie albo uzyskania dostępu do zasobu, poczekaj, aż zasób zwolnione i uzyskać dostęp lub poczekaj, aż zasób, które mogą być wprowadzane i limit czasu, w których nie można uzyskać dostęp do zasobu. W każdym przypadku zasobu uzyskano dostęp w sposób bezpieczny dla wątków. Do zwolnienia zasobu, użyj obiektu blokady `Unlock` funkcja elementu członkowskiego (na przykład [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), lub zezwalać na obiekt blokady do wykraczać poza zakres.

Aby uzyskać więcej informacji na temat korzystania z `CMutex` obiektów, zobacz artykuł [wielowątkowość: Jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

##  <a name="cmutex"></a>  CMutex::CMutex

Konstruuje nazwane i nienazwane `CMutex` obiektu.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
Określa, jeśli tworzenia wątku `CMutex` obiektu początkowo ma dostęp do zasobu, kontrolowane przez element mutex.

*lpszName*<br/>
Nazwa `CMutex` obiektu. Jeśli istnieje inny element mutex o takiej samej nazwie, *lpszName* musi zostać dostarczony, jeśli obiekt ma być używany przez granice procesu. Jeśli **NULL**, element mutex nie będą mieć nazwy. Jeśli nazwa pasuje do istniejącego obiektu mutex, Konstruktor tworzy nową `CMutex` obiektu, który odwołuje się element mutex o takiej nazwie. Jeśli nazwa jest zgodna z istniejącym obiektem synchronizacji nie jest mutex, konstrukcja nie powiedzie się.

*lpsaAttribute*<br/>
Atrybuty zabezpieczeń dla obiektu mutex. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Dostęp i zwalniania `CMutex` obiektu, Utwórz [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu, a następnie wywołać jej [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) Funkcje Członkowskie. Jeśli `CMutex` obiekt jest używany autonomiczny, wywoływanie jej `Unlock` funkcja elementu członkowskiego do jego zwolnienia.

> [!IMPORTANT]
>  Po utworzeniu `CMutex` obiektu, należy użyć [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) aby upewnić się, że element mutex już nie istnieje. Jeśli element mutex istniał nieoczekiwanie, może to oznaczać, nieautoryzowany proces zajmowanie i może zamierza użyć obiektu mutex złośliwie. W tym przypadku zalecaną procedurą zabezpieczenia jest zamknąć dojścia i kontynuować tak, jakby wystąpił błąd podczas tworzenia obiektu.

## <a name="see-also"></a>Zobacz także

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
