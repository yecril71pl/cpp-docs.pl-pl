---
title: Klasa CCmdUI
ms.date: 09/06/2019
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
ms.openlocfilehash: 3e167d9e305481e05808f5e553222c10abbc88de
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752728"
---
# <a name="ccmdui-class"></a>Klasa CCmdUI

Jest używany tylko `ON_UPDATE_COMMAND_UI` w `CCmdTarget`ramach programu obsługi w klasie pochodnej.

## <a name="syntax"></a>Składnia

```
class CCmdUI
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|Informuje mechanizm routingu poleceń, aby kontynuować routing bieżącej wiadomości w dół łańcucha obsługi.|
|[CCmdUI::Włącz](#enable)|Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.|
|[CCmdUI::SetCheck](#setcheck)|Ustawia stan wyboru elementu interfejsu użytkownika dla tego polecenia.|
|[CCmdUI::SetRadio](#setradio)|Podobnie `SetCheck` jak funkcja członkowna, ale działa na grupach radiowych.|
|[CCmdUI::SetText](#settext)|Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|Identyfikator obiektu interfejsu użytkownika.|
|[CCmdUI::m_nIndex](#m_nindex)|Indeks obiektu interfejsu użytkownika.|
|[CCmdUI::m_pMenu](#m_pmenu)|Wskazuje menu reprezentowane przez `CCmdUI` obiekt.|
|[CCmdUI::m_pOther](#m_pother)|Wskazuje obiekt okna, który wysłał powiadomienie.|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|Wskazuje zawarte podmenu reprezentowane przez `CCmdUI` obiekt.|

## <a name="remarks"></a>Uwagi

`CCmdUI`nie ma klasy podstawowej.

Gdy użytkownik aplikacji ściąga menu, każdy element menu musi wiedzieć, czy powinien być wyświetlany jako włączone lub wyłączone. Miejsce docelowe polecenia menu zawiera te informacje, implementując program obsługi ON_UPDATE_COMMAND_UI. Dla każdego polecenia interfejsu użytkownika obiektów w aplikacji, użyj [Kreatora klas](mfc-class-wizard.md) lub **właściwości** okna (w **widoku klasy),** aby utworzyć wpis mapy wiadomości i prototyp funkcji dla każdego programu obsługi.

Gdy menu jest ściągane w dół, struktura wyszukuje i wywołuje `CCmdUI` każdego ON_UPDATE_COMMAND_UI `Enable` `Check`obsługi, każdy program obsługi wywołuje funkcje członkowskie, takie jak i , a struktura następnie odpowiednio wyświetla każdy element menu.

Element menu można zastąpić przyciskiem paska sterowania lub innym obiektem interfejsu `ON_UPDATE_COMMAND_UI` użytkownika polecenia bez zmiany kodu w programie obsługi.

W poniższej tabeli `CCmdUI`podsumowano wpływ funkcji członkowskich na różne elementy interfejsu użytkownika polecenia.

|Element interfejsu użytkownika|Włączanie|Sprawdzanie zestawu|SetRadio ( SetRadio )|Settext|
|--------------------------|------------|--------------|--------------|-------------|
|Pozycja menu|Włącza lub wyłącza|Sprawdza lub odznacza|Sprawdza przy użyciu kropki|Ustawia tekst elementu|
|Przycisk paska narzędzi|Włącza lub wyłącza|Zaznacza, nie wybiera lub nieokreślone|Tak samo jak`SetCheck`|(Nie dotyczy)|
|Okienko paska stanu|Sprawia, że tekst jest widoczny lub niewidoczny|Ustawia wyskakujące lub normalne obramowanie|Tak samo jak`SetCheck`|Ustawia tekst okienka|
|Przycisk Normalny w`CDialogBar`|Włącza lub wyłącza|Pole wyboru Sprawdza lub odznacza|Tak samo jak`SetCheck`|Ustawia tekst przycisku|
|Normalna kontrola w`CDialogBar`|Włącza lub wyłącza|(Nie dotyczy)|(Nie dotyczy)|Ustawia tekst okna|

Aby uzyskać więcej informacji na temat używania tej klasy, zobacz [Jak zaktualizować obiekty interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CCmdUI`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::ContinueRouting

Wywołanie tej funkcji elementu członkowskiego, aby poinformować mechanizm routingu polecenia, aby kontynuować routing bieżącej wiadomości w dół łańcucha obsługi.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>Uwagi

Jest to funkcja zaawansowanego elementu członkowskiego, która powinna być używana w połączeniu z ON_COMMAND_EX program obsługi, który zwraca FALSE. Aby uzyskać więcej informacji, zobacz [Uwaga techniczna 6](../../mfc/tn006-message-maps.md).

## <a name="ccmduienable"></a><a name="enable"></a>CCmdUI::Włącz

Wywołanie tej funkcji elementu członkowskiego, aby włączyć lub wyłączyć element interfejsu użytkownika dla tego polecenia.

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
PRAWDA, aby włączyć element, FALSE, aby go wyłączyć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI::m_nID

Identyfikator elementu menu, przycisku paska narzędzi lub innego obiektu interfejsu `CCmdUI` użytkownika reprezentowanego przez obiekt.

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI::m_nIndex

Indeks elementu menu, przycisku paska narzędzi lub innego obiektu `CCmdUI` interfejsu użytkownika reprezentowanego przez obiekt.

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CCmdUI::m_pMenu

Wskaźnik `CMenu` (typu) do menu reprezentowanego `CCmdUI` przez obiekt.

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>Uwagi

NULL, jeśli element nie jest menu.

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CCmdUI::m_pSubMenu

Wskaźnik `CMenu` (typu) do zamkniętego podmenu reprezentowanego przez `CCmdUI` obiekt.

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>Uwagi

NULL, jeśli element nie jest menu. Jeśli menu podrzędne jest wyskakującym *okienkiem, m_nID* zawiera identyfikator pierwszego elementu w wyskakującym menu. Aby uzyskać więcej informacji, zobacz [uwaga techniczna 21](../../mfc/tn021-command-and-message-routing.md).

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CCmdUI::m_pOther

Wskaźnik (typu) `CWnd`do obiektu okna, takiego jak narzędzie lub pasek stanu, który wysłał powiadomienie.

```
CWnd* m_pOther;
```

### <a name="remarks"></a>Uwagi

NULL, jeśli element jest menu `CWnd` lub obiekt nie-.

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CCmdUI::SetCheck

Wywołanie tej funkcji elementu członkowskiego, aby ustawić element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu wyboru.

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>Parametry

*nSprawda*<br/>
Określa stan sprawdzania do ustawionego. Jeśli 0, odznacza; jeżeli 1, kontrole; a jeśli 2, ustawia nieokreślony.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego działa w przypadku elementów menu i przycisków paska narzędzi. Stan nieokreślony dotyczy tylko przycisków paska narzędzi.

## <a name="ccmduisetradio"></a><a name="setradio"></a>CCmdUI::SetRadio

Wywołanie tej funkcji elementu członkowskiego, aby ustawić element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu wyboru.

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
PRAWDA, aby włączyć element; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu `SetCheck`członkowskiego działa jak , z tą różnicą, że działa na elementach interfejsu użytkownika działających jako część grupy radiowej. Odznaczanie innych elementów w grupie nie jest automatyczne, chyba że same elementy zachowują zachowanie grupy radiowej.

## <a name="ccmduisettext"></a><a name="settext"></a>CCmdUI::SetText

Wywołanie tej funkcji elementu członkowskiego, aby ustawić tekst elementu interfejsu użytkownika dla tego polecenia.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Wskaźnik do ciągu tekstowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)
