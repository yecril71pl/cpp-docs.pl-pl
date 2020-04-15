---
title: Klasa CDockState
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: 1c76bcda6465ca86b8da4778d3653cb23001b78b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375555"
---
# <a name="cdockstate-class"></a>Klasa CDockState

Klasa serializowana, `CObject` która ładuje, zwalnia lub czyści stan jednego lub więcej pasków sterujących dokowania w pamięci trwałej (pliku).

## <a name="syntax"></a>Składnia

```
class CDockState : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockState::Wyczyść](#clear)|Czyści informacje o stanie stacji dokującej.|
|[CDockState::GetVersion](#getversion)|Pobiera numer wersji przechowywanego stanu paska.|
|[CDockState::LoadState](#loadstate)|Pobiera informacje o stanie z rejestru lub . ini.|
|[CDockState::Zapisz stan](#savestate)|Zapisuje informacje o stanie w rejestrze lub pliku INI.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Tablica wskaźników do przechowywanych informacji o stanie stacji dokującej z jednym wpisem dla każdego paska sterowania.|

## <a name="remarks"></a>Uwagi

Stan stacji dokującej obejmuje rozmiar i położenie pręta oraz to, czy jest zadokowany. Podczas pobierania stanu przechowywanej `CDockState` stacji dokującej sprawdza położenie pręta i, jeśli pasek `CDockState` nie jest widoczny z bieżącymi ustawieniami ekranu, skaluje położenie pręta tak, aby był widoczny. Głównym celem `CDockState` jest utrzymanie całego stanu liczby prętów kontrolnych i umożliwienie zapisywania i ładowania tego stanu do rejestru, aplikacji . pliku INI lub w postaci binarnej `CArchive` jako część zawartości obiektu.

Pasek może być dowolnym paskiem sterowania dokowania, w tym paskiem narzędzi, paskiem stanu lub paskiem dialogowym. `CDockState`obiekty są zapisywane i odczytywane `CArchive` do lub z pliku za pośrednictwem obiektu.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) pobiera informacje o stanie wszystkich `CControlBar` obiektów okna ramki `CDockState` i umieszcza go w obiekcie. Następnie można zapisać zawartość `CDockState` obiektu do magazynu za pomocą [Serialize](../../mfc/reference/cobject-class.md#serialize) lub [CDockState::SaveState](#savestate). Jeśli później chcesz przywrócić stan prętów sterujących w oknie ramki, `Serialize` można załadować stan z [cDockState:::LoadState](#loadstate), a następnie użyć [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) zastosować zapisany stan do pasków sterujących okna ramki.

Aby uzyskać więcej informacji na temat pasków sterowania dokowania, zobacz artykuły [Paski sterowania](../../mfc/control-bars.md), [Paski narzędzi: Dokowanie i pływające](../../mfc/docking-and-floating-toolbars.md), i [Ramka Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState::Wyczyść

Wywołanie tej funkcji, aby wyczyścić `CDockState` wszystkie informacje dokowania przechowywane w obiekcie.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Obejmuje to nie tylko to, czy pasek jest zadokowany, czy nie, ale także rozmiar i położenie baru oraz to, czy jest widoczny.

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState::GetVersion

Wywołanie tej funkcji, aby pobrać numer wersji przechowywanego stanu paska.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

1, jeśli zapisane informacje o pasku są starsze niż bieżący stan słupka; 2, jeśli zapisane informacje o pasku są takie same jak bieżący stan paska.

### <a name="remarks"></a>Uwagi

Obsługa wersji umożliwia poprawiony pasek, aby dodać nowe trwałe właściwości i nadal być w stanie wykryć i załadować stan trwały utworzony przez wcześniejszą wersję paska.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState::LoadState

Wywołanie tej funkcji, aby pobrać informacje o stanie z rejestru lub . ini.

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Wskazuje ciąg o zerowej teminacji, który określa nazwę sekcji w pliku inicjowania lub klucz w rejestrze systemu Windows, w którym są przechowywane informacje o stanie.

### <a name="remarks"></a>Uwagi

Nazwa profilu jest sekcją aplikacji . plik INI lub rejestr zawierający informacje o stanie słupków. Informacje o stanie paska sterowania można zapisać w rejestrze lub . PLIK INI `SaveState`z plikiem .

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo

Obiekt, `CPtrArray` który jest tablicą wskaźników do przechowywanych informacji paska sterowania dla `CDockState` każdego paska sterowania, który ma zapisane informacje o stanie w obiekcie.

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState::Zapisz stan

Wywołanie tej funkcji, aby zapisać informacje o stanie w rejestrze lub . ini.

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Wskazuje ciąg o zerowej teminacji, który określa nazwę sekcji w pliku inicjowania lub klucz w rejestrze systemu Windows, w którym są przechowywane informacje o stanie.

### <a name="remarks"></a>Uwagi

Nazwa profilu jest sekcją aplikacji . plik INI lub rejestr zawierający informacje o stanie paska sterowania. `SaveState`zapisuje również bieżący rozmiar ekranu. Można pobrać informacje o pasku sterowania z rejestru lub . PLIK INI `LoadState`z plikiem .

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
