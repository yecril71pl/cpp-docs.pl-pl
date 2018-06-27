---
title: Klasa CDockState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
dev_langs:
- C++
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83ae0a746e31c211517563a018e5b7da18e3350a
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955599"
---
# <a name="cdockstate-class"></a>Klasa CDockState
Zserializowany `CObject` klasy, która ładuje, zwalnia lub czyści stanu przynajmniej jednej formantu dokowania pasków w pamięci trwałej (plik).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDockState : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDockState::Clear](#clear)|Usuwa informacje o stanie dokowania.|  
|[CDockState::GetVersion](#getversion)|Pobiera numer wersji zapisana pasek stanu.|  
|[CDockState::LoadState](#loadstate)|Pobiera stan informacji z rejestru lub. Pliku INI.|  
|[CDockState::SaveState](#savestate)|Zapisuje informacje o stanie do rejestru lub pliku INI.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Dock — tablicy wskaźników do przechowywanych informacji o stanie dla każdego pasek sterowania jeden wpis.|  
  
## <a name="remarks"></a>Uwagi  
 Stan dokowania obejmuje rozmiar i położenie paska i czy jest zadokowany. Podczas pobierania zapisana dock stanu, `CDockState` sprawdza pasek pozycji i, jeśli pasek nie jest widoczna przy bieżących ustawieniach ekranu `CDockState` skaluje pasek pozycji tak, aby była widoczna. Głównym celem `CDockState` jest przechowuje stanu cały szereg paski sterowania i umożliwić tego stanu do zapisania i ładowane do, aplikacja w rejestrze. Plik INI, lub w postaci binarnej jako część `CArchive` zawartości obiektu.  
  
 Pasek może być dowolny formant dokującego paska narzędzi, pasek stanu lub paska dialogowego w tym. `CDockState` obiekty są zapisywane i odczytu do lub z pliku za pośrednictwem `CArchive` obiektu.  
  
 [CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) pobiera informacje o stanie wszystkie ramki okna w `CControlBar` obiekty i umieszczenie go w `CDockState` obiektu. Następnie można zapisać zawartość `CDockState` obiektu magazynu z [serializacja](../../mfc/reference/cobject-class.md#serialize) lub [CDockState::SaveState](#savestate). Jeśli chcesz później przywrócić stan paski kontrolki w oknie ramowym, można załadować stanu z `Serialize` lub [CDockState::LoadState](#loadstate), następnie użyć [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) dotyczyć zapisanego stan do pasków sterowania ramkę okna.  
  
 Aby uzyskać więcej informacji dotyczących dokujące paski sterowania, zobacz artykuły [paski sterowania](../../mfc/control-bars.md), [paski narzędzi: zadokowane i przestawne](../../mfc/docking-and-floating-toolbars.md), i [okien ramowych](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxadv.h  
  
##  <a name="clear"></a>  CDockState::Clear  
 Wywołanie tej funkcji, aby wyczyścić wszystkie dokowania informacje przechowywane w `CDockState` obiektu.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Obejmuje to nie tylko czy pasku jest zadokowany lub nie, ale rozmiar i położenie paska i czy jest on widoczny.  
  
##  <a name="getversion"></a>  CDockState::GetVersion  
 Wywołanie tej funkcji można pobrać numeru wersji zapisana pasek stanu.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 1, gdy pasek przechowywanych informacji jest starsza niż bieżąca pasek stanu; Jeśli 2 pasku przechowywanych informacji jest taka sama jak bieżący pasek stanu.  
  
### <a name="remarks"></a>Uwagi  
 Obsługa wersji umożliwia pasek poprawione do dodawania nowych właściwości trwałych i nadal mieć możliwość wykrywania i załadować trwały stan utworzony we wcześniejszej wersji paska.  
  
##  <a name="loadstate"></a>  CDockState::LoadState  
 Wywołanie tej funkcji można pobrać informacji o stanie z rejestru lub. Pliku INI.  
  
```  
void LoadState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszProfileName*  
 Wskazuje teminated pusty ciąg, który określa nazwę sekcji w pliku inicjującego lub klucza rejestru systemu Windows, w którym są przechowywane informacje o stanie.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa profilu jest części aplikacji. Plik INI lub rejestru, który zawiera informacje o stanie paski. Kontrolki paska informacji o stanie można zapisać w rejestrze lub. Plik INI o `SaveState`.  
  
##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo  
 A `CPtrArray` obiekt, który jest tablicy wskaźników do informacji pasek sterowania przechowywanych dla każdego pasek sterowania, który został zapisany informacje o stanie w `CDockState` obiektu.  
  
```  
CPtrArray m_arrBarInfo;  
```  
  
##  <a name="savestate"></a>  CDockState::SaveState  
 Wywołanie tej funkcji, aby zapisać informacje o stanie w rejestrze lub. Pliku INI.  
  
```  
void SaveState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszProfileName*  
 Wskazuje teminated pusty ciąg, który określa nazwę sekcji w pliku inicjującego lub klucza rejestru systemu Windows, w którym są przechowywane informacje o stanie.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa profilu jest części aplikacji. Plik INI lub rejestru zawierającego informacje o stanie pasek sterowania. `SaveState` pozwalają również zmniejszyć rozmiar bieżącego ekranu. Informacje dotyczące pasek sterowania można pobrać z rejestru lub. Plik INI o `LoadState`.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)

