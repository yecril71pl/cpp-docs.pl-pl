---
title: Klasa CUserTool
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: b73cb3d3c6e244a9aa41a91a3ee9ff1efa98d496
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502244"
---
# <a name="cusertool-class"></a>Klasa CUserTool

Narzędzie użytkownika to element menu, w którym jest uruchamiana aplikacja zewnętrzna. Karta **Narzędzia** okna dialogowego **Dostosowywanie** ( [Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umożliwia użytkownikowi dodawanie narzędzi użytkownika i Określanie nazwy, polecenia, argumentów i katalogu początkowego dla każdego narzędzia użytkownika.

## <a name="syntax"></a>Składnia

```
class CUserTool : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::D rawToolIcon](#drawtoolicon)|Rysuje ikonę narzędzia użytkownika w określonym prostokącie.|
|[CUserTool:: Get— polecenie](#getcommand)|Zwraca ciąg zawierający tekst polecenia skojarzonego z narzędziem użytkownika.|
|[CUserTool::GetCommandId](#getcommandid)|Zwraca identyfikator polecenia elementu menu narzędzia użytkownika.|
|[CUserTool:: Invoke](#invoke)|Wykonuje polecenie skojarzone z narzędziem użytkownika.|
|[CUserTool:: serializować](#serialize)|Odczytuje lub zapisuje ten obiekt z lub do archiwum. (Przesłania [CObject:: serializować](../../mfc/reference/cobject-class.md#serialize)).|
|[CUserTool:: Set— polecenie](#setcommand)|Ustawia polecenie skojarzone z narzędziem użytkownika.|
|[CUserTool::SetToolIcon](#settoolicon)|Ładuje ikonę narzędzia użytkownika z aplikacji skojarzonej z tym narzędziem.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Ładuje ikonę domyślną dla narzędzia użytkownika.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty wiersza polecenia dla narzędzia użytkownika.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Początkowy katalog dla narzędzia użytkownika.|
|[CUserTool::m_strLabel](#m_strlabel)|Nazwa narzędzia, która jest wyświetlana w elemencie menu dla narzędzia.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat włączania narzędzi użytkownika w aplikacji, zobacz [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak utworzyć narzędzie z `CUserToolsManager` obiektu, `m_strLabel` ustawić zmienną członkowską i ustawić aplikację, która jest uruchamiana za pomocą narzędzia użytkownika. Ten fragment kodu jest częścią [przykładu demonstracyjnego Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertool. h

##  <a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="drawtoolicon"></a>CUserTool::D rawToolIcon

Rysuje ikonę narzędzia użytkownika w środku określonego prostokąta.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Wskaźnik do kontekstu urządzenia.

*rectImage*<br/>
podczas Określa współrzędne obszaru, aby wyświetlić ikonę.

##  <a name="getcommand"></a>CUserTool:: Get— polecenie

Zwraca ciąg zawierający tekst polecenia skojarzonego z narzędziem użytkownika.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiektu, który zawiera tekst polecenia skojarzonego z narzędziem użytkownika.

##  <a name="getcommandid"></a>CUserTool::GetCommandId

Zwraca identyfikator polecenia narzędzia użytkownika.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia tego narzędzia użytkownika.

##  <a name="invoke"></a>CUserTool:: Invoke

Wykonuje polecenie skojarzone z narzędziem użytkownika.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli polecenie zostało wykonane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołuje interfejs [API](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) , aby wykonać polecenie skojarzone z narzędziem użytkownika. Funkcja kończy się niepowodzeniem, jeśli polecenie jest puste lub jeśli interfejs [API](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) nie powiedzie się.

##  <a name="loaddefaulticon"></a>CUserTool::LoadDefaultIcon

Ładuje ikonę domyślną dla narzędzia użytkownika.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do załadowanej ikony (HICON) lub wartość NULL, jeśli nie można załadować ikony domyślnej.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy nie może załadować ikony dla narzędzia zdefiniowanego przez użytkownika z pliku wykonywalnego narzędzia.

Zastąp tę metodę, aby podać własną ikonę narzędzia.

##  <a name="m_strarguments"></a>CUserTool::m_strArguments

Argumenty wiersza polecenia dla narzędzia użytkownika.

```
CString m_strArguments;
```

### <a name="remarks"></a>Uwagi

Ten ciąg jest przesyłany do narzędzia po wywołaniu [CUserTool:: Invoke](#invoke) lub gdy użytkownik kliknie polecenie skojarzone z tym narzędziem.

##  <a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

Określa katalog początkowy narzędzia użytkownika.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Uwagi

Ta zmienna określa katalog początkowy, który wykonuje narzędzie w przypadku wywołania [CUserTool:: Invoke](#invoke) lub kiedy użytkownik kliknie polecenie skojarzone z tym narzędziem.

##  <a name="m_strlabel"></a>CUserTool::m_strLabel

Etykieta wyświetlana w elemencie menu dla narzędzia.

```
CString m_strLabel;
```

##  <a name="serialize"></a>CUserTool:: serializować

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

podczas *AR*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setcommand"></a>CUserTool:: Set— polecenie

Ustawia aplikację, która jest uruchamiana za pomocą narzędzia użytkownika.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parametry

*lpszCmd*<br/>
podczas Określa nową aplikację, która ma zostać skojarzona z narzędziem użytkownika.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ustawić nową aplikację, która jest uruchamiana w narzędziu użytkownika. Metoda niszczy starą ikonę i ładuje nową ikonę z danej aplikacji. Jeśli nie można załadować ikony z aplikacji, zostanie załadowana ikona domyślna narzędzia użytkownika przez wywołanie [CUserTool:: LoadDefaultIcon](#loaddefaulticon).

##  <a name="settoolicon"></a>CUserTool::SetToolIcon

Ładuje ikonę narzędzia użytkownika z aplikacji używanej przez narzędzie.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do załadowanej ikony.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby załadować ikonę, która ma być wyświetlana w elemencie menu. Ta metoda wyszukuje ikonę w pliku wykonywalnym, którego używa narzędzie. Jeśli nie ma ikony domyślnej, zamiast niej zostanie użyta ikona podana przez [CUserTool:: LoadDefaultIcon](#loaddefaulticon) .

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Klasa CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
