---
title: Klasa CCmdUI
ms.date: 11/04/2016
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: c1d44638779f9b5caf052106ac172110d309b69f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206388"
---
# <a name="ccmdui-class"></a>Klasa CCmdUI

Jest używana tylko wewnątrz `ON_UPDATE_COMMAND_UI` obsługi w `CCmdTarget`-klasy pochodnej.

## <a name="syntax"></a>Składnia

```
class CCmdUI
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|Informuje mechanizm routingu poleceń, aby kontynuować, routing do bieżącej wiadomości w łańcuchu obsługi.|
|[CCmdUI::Enable](#enable)|Włącza lub wyłącza elementu interfejsu użytkownika dla tego polecenia.|
|[CCmdUI::SetCheck](#setcheck)|Ustawia stan wyboru elementu interfejsu użytkownika dla tego polecenia.|
|[CCmdUI::SetRadio](#setradio)|Podobnie jak `SetCheck` funkcja elementu członkowskiego, ale działa na grup przycisków opcji.|
|[CCmdUI::SetText](#settext)|Ustawia tekst dla elementu interfejsu użytkownika dla tego polecenia.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|Identyfikator obiektu interfejsu użytkownika.|
|[CCmdUI::m_nIndex](#m_nindex)|Indeks obiektu interfejsu użytkownika.|
|[CCmdUI::m_pMenu](#m_pmenu)|Wskazuje na menu, reprezentowane przez `CCmdUI` obiektu.|
|[CCmdUI::m_pOther](#m_pother)|Wskazuje obiekt okna, które wysłane powiadomienie.|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Wskazuje zawartej podmenu, reprezentowane przez `CCmdUI` obiektu.|

## <a name="remarks"></a>Uwagi

`CCmdUI` nie ma klasy bazowej.

Gdy użytkownik aplikacji ściąga menu, każdego menu elementu musi wiedzieć, czy ma być wyświetlany jako włączone lub wyłączone. Element docelowy polecenia menu udostępnia te informacje poprzez implementację programu obsługi ON_UPDATE_COMMAND_UI. Dla każdego polecenia obiektów interfejsu użytkownika w aplikacji umożliwia utworzenie prototypu mapy komunikatów wejścia i funkcja obsługi każdego okna właściwości.

Gdy jest obniżona, menu, struktura wyszukuje i wywołuje program obsługi każdego ON_UPDATE_COMMAND_UI, każdy program obsługi wywołania `CCmdUI` takich jak funkcje Członkowskie `Enable` i `Check`, i platformę odpowiednio wyświetla każdy element menu.

Element menu, można zastąpić przycisk paska sterowania lub inny obiekt interfejsu użytkownika polecenia bez konieczności zmiany kodu w ramach `ON_UPDATE_COMMAND_UI` programu obsługi.

W poniższej tabeli zestawiono wpływ `CCmdUI`przez funkcje Członkowskie mają na różne elementy interfejsu użytkownika polecenia.

|Element interfejsu użytkownika|Włącz|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Element menu|Włącza lub wyłącza|Sprawdza, czy lub usuwa zaznaczenie|Umożliwia sprawdzenie za pomocą pojedynczego znaku kropki|Ustawia element tekstu|
|Przycisk paska narzędzi|Włącza lub wyłącza|Wybiera, usuwa, lub nieokreślony|Takie same jak `SetCheck`|(Nie dotyczy)|
|W okienku paska stanu|Sprawia, że tekst widoczny lub niewidoczny|Ustawia wyskakujący lub normal obramowania|Takie same jak `SetCheck`|Ustawia okienko tekstu|
|Normalny przycisk `CDialogBar`|Włącza lub wyłącza|Sprawdza, czy lub usuwa zaznaczenie pola wyboru|Takie same jak `SetCheck`|Ustawia przycisk tekstu|
|Kontrolka normalna w `CDialogBar`|Włącza lub wyłącza|(Nie dotyczy)|(Nie dotyczy)|Ustawia tekst okna|

Aby uzyskać więcej informacji dotyczących używania tej klasy, zobacz [jak obiektów interfejsu użytkownika aktualizacji](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CCmdUI`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting

Wywołaj tę funkcję elementu członkowskiego, aby poinformować mechanizm routingu poleceń, aby kontynuować, routing do bieżącej wiadomości w łańcuchu obsługi.

```
void ContinueRouting();
```

### <a name="remarks"></a>Uwagi

Jest to funkcja członków na poziomie zaawansowanym, który ma zostać użyty w połączeniu z programem obsługi ON_COMMAND_EX, która zwraca wartość FALSE. Aby uzyskać więcej informacji, zobacz [techniczne Uwaga 6](../../mfc/tn006-message-maps.md).

##  <a name="enable"></a>  CCmdUI::Enable

Wywołaj tę funkcję elementu członkowskiego, aby włączyć lub wyłączyć elementu interfejsu użytkownika dla tego polecenia.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
Wartość TRUE powoduje włączenie elementu wartość FALSE, aby je wyłączyć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>  CCmdUI::m_nID

Identyfikator elementu menu, przycisk paska narzędzi lub inny obiekt interfejsu użytkownika, reprezentowane przez `CCmdUI` obiektu.

```
UINT m_nID;
```

##  <a name="m_nindex"></a>  CCmdUI::m_nIndex

Indeks elementu menu, przycisk paska narzędzi lub inny obiekt interfejsu użytkownika, reprezentowane przez `CCmdUI` obiektu.

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>  CCmdUI::m_pMenu

Wskaźnik (z `CMenu` typu) do menu, reprezentowane przez `CCmdUI` obiektu.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Uwagi

Wartość NULL, jeśli element nie znajduje się menu.

##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu

Wskaźnik (z `CMenu` typu) do zamkniętego podmenu, reprezentowane przez `CCmdUI` obiektu.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Uwagi

Wartość NULL, jeśli element nie znajduje się menu. W przypadku pod menu wyskakującego okienka, *m_nID* zawiera identyfikator pierwszego elementu w menu podręcznym. Aby uzyskać więcej informacji, zobacz [techniczne 21 Uwaga](../../mfc/tn021-command-and-message-routing.md).

##  <a name="m_pother"></a>  CCmdUI::m_pOther

Wskaźnik (typu `CWnd`) do obiektu okna, takie jak narzędzia lub paska stanu, które wysłane powiadomienie.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Uwagi

Wartość NULL, jeśli element znajduje się menu lub innej niż `CWnd` obiektu.

##  <a name="setcheck"></a>  CCmdUI::SetCheck

Wywołanie tej funkcji elementu członkowskiego, aby ustawić stan zaznaczenia odpowiednich elementu interfejsu użytkownika dla tego polecenia.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parametry

*nCheck*<br/>
Określa stan wyboru, aby ustawić. Jeśli 0, usuwa zaznaczenie; Jeśli 1, sprawdza, czy; i jeśli jest to 2, ustawia nieokreślony.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego działa w przypadku elementów menu i przycisków na pasku narzędzi. Stan nieokreślony stosuje tylko przyciski paska narzędzi.

##  <a name="setradio"></a>  CCmdUI::SetRadio

Wywołanie tej funkcji elementu członkowskiego, aby ustawić stan zaznaczenia odpowiednich elementu interfejsu użytkownika dla tego polecenia.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
Wartość TRUE, aby włączyć element; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego działa jak `SetCheck`, z tą różnicą, że działa na elementach interfejsu użytkownika, działając jako część grupy radio. Usunięcie zaznaczenia elementów grupy nie jest automatyczne, chyba że same elementy zapewnić odpowiednie zachowanie grupa opcji.

##  <a name="settext"></a>  CCmdUI::SetText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić tekst elementu interfejsu użytkownika dla tego polecenia.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Wskaźnik do ciągu tekstowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
