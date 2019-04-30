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
ms.openlocfilehash: b8c4b80d7182795d8919adb64491d506325976ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391182"
---
# <a name="cdockstate-class"></a>Klasa CDockState

Zserializowany obiekt `CObject` klasę, która ładuje, zwalnia lub czyści stan formantu dokowania jeden lub więcej pasków w trwałej pamięci (plik).

## <a name="syntax"></a>Składnia

```
class CDockState : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDockState::Clear](#clear)|Usuwa informacje o stanie dokowania.|
|[CDockState::GetVersion](#getversion)|Pobiera numer wersji przechowywany pasek stanu.|
|[CDockState::LoadState](#loadstate)|Pobiera stan informacji z rejestru lub. Pliku INI.|
|[CDockState::SaveState](#savestate)|Zapisuje informacje o stanie do rejestru lub pliku INI.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Tablica wskaźników do przechowywanej zadokować jeden wpis dla każdego formantu paska informacji o stanie.|

## <a name="remarks"></a>Uwagi

Stan dokowania zawiera, rozmiar i położenie paska i czy jest zadokowany. Podczas pobierania przechowywaną zadokować stanu, `CDockState` sprawdza, czy pasek pozycji i, jeśli pasek nie jest widoczny z bieżącymi ustawieniami ekranu `CDockState` skaluje pasek pozycji tak, aby była widoczna. Głównym celem `CDockState` jest do przechowywania stanu cały szereg paski sterowania i umożliwienie tego stanu można zapisać i załadować do rejestru, aplikacja. Plik INI, lub w formacie binarnym w ramach `CArchive` zawartości obiektu.

Pasek może być dowolną dokowalne kontrolkę paska narzędzi, pasek stanu lub Pasek dialogowy w tym. `CDockState` obiekty są zapisywane i odczytu do lub z pliku za pośrednictwem `CArchive` obiektu.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) pobiera informacje o stanie wszystkie ramki okna firmy `CControlBar` obiektów i umieszcza go w `CDockState` obiektu. Następnie można napisać zawartość `CDockState` obiektu do magazynu przy użyciu [Serialize](../../mfc/reference/cobject-class.md#serialize) lub [CDockState::SaveState](#savestate). Jeśli chcesz później przywrócić stan pasków sterowania w oknie ramki, można załadować stanu z `Serialize` lub [CDockState::LoadState](#loadstate), następnie za pomocą [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) zastosować zapisane stan do pasków sterowania oknem ramki.

Aby uzyskać więcej informacji na temat dokowania pasków sterowania, zobacz artykuły [paski sterowania](../../mfc/control-bars.md), [paski narzędzi: Zadokowane i przestawne](../../mfc/docking-and-floating-toolbars.md), i [ramki Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

Wywołaj tę funkcję, aby wyczyścić wszystkie dokowania informacje przechowywane w `CDockState` obiektu.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Obejmuje to nie tylko czy pasek jest zadokowany lub nie, ale rozmiar i położenie paska i czy jest on widoczny.

##  <a name="getversion"></a>  CDockState::GetVersion

Wywołaj tę funkcję, aby pobrać numer wersji przechowywany pasek stanu.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Wartość zwracana

1, jeśli pasek przechowywane informacje są starsze niż bieżący pasek stanu; 2, jeśli pasek przechowywanych informacji jest taka sama jak bieżący pasek stanu.

### <a name="remarks"></a>Uwagi

Obsługa wersji umożliwia poprawione pasek dodawać nowe właściwości trwałe i nadal mieć możliwość wykrywania i załadować trwały stan utworzone przy użyciu wcześniejszej wersji paska.

##  <a name="loadstate"></a>  CDockState::LoadState

Wywołaj tę funkcję, aby pobrać informacje o stanie z rejestru lub. Pliku INI.

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Wskazuje ciąg teminated o wartości null, który określa nazwę sekcji w pliku inicjującego lub klucza w rejestrze Windows, w którym są przechowywane informacje o stanie.

### <a name="remarks"></a>Uwagi

Nazwa profilu jest części aplikacji. Plik INI lub rejestru, który zawiera informacje o stanie paski. Kontrolki paska informacji o stanie można zapisać do rejestru lub. Plik INI, za pomocą `SaveState`.

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

A `CPtrArray` obiekt, który jest tablicą wskaźników o pasek sterowania przechowywanych dla każdego pasek sterowania, który został zapisany informacje o stanie w `CDockState` obiektu.

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

Wywołaj tę funkcję, aby zapisać informacje o stanie do rejestru lub. Pliku INI.

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
Wskazuje ciąg teminated o wartości null, który określa nazwę sekcji w pliku inicjującego lub klucza w rejestrze Windows, w którym są przechowywane informacje o stanie.

### <a name="remarks"></a>Uwagi

Nazwa profilu jest części aplikacji. Plik INI lub rejestr zawierający informacje o stanie paska sterowania. `SaveState` Ponadto zapisuje bieżący rozmiar ekranu. Informacje dotyczące paska sterowania można pobrać z rejestru lub. Plik INI, za pomocą `LoadState`.

## <a name="see-also"></a>Zobacz także

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
