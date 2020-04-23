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
ms.openlocfilehash: 183b30961e4a7d3079fa0d035a4ddc38bc2eebac
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752032"
---
# <a name="cusertool-class"></a>Klasa CUserTool

Narzędzie użytkownika jest elementem menu, który uruchamia aplikację zewnętrzną. Karta **Narzędzia** w oknie dialogowym **Dostosowywanie** [(CMFCToolBarsCustomizeDialog Class)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)umożliwia użytkownikowi dodawanie narzędzi użytkownika oraz określanie nazwy, polecenia, argumentów i katalogu początkowego dla każdego narzędzia użytkownika.

## <a name="syntax"></a>Składnia

```
class CUserTool : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Rysuje ikonę narzędzia użytkownika w określonym prostokącie.|
|[CUserTool::GetCommand](#getcommand)|Zwraca ciąg zawierający tekst polecenia skojarzonego z narzędziem użytkownika.|
|[CUserTool::GetCommandId](#getcommandid)|Zwraca identyfikator polecenia elementu menu narzędzia użytkownika.|
|[CUserTool::Wywołaj](#invoke)|Wykonuje polecenie skojarzone z narzędziem użytkownika.|
|[CUserTool::Serialize](#serialize)|Odczytuje lub zapisuje ten obiekt z lub do archiwum. (Zastępuje [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Ustawia polecenie skojarzone z narzędziem użytkownika.|
|[CUserTool::SetToolIcon](#settoolicon)|Ładuje ikonę narzędzia użytkownika z aplikacji skojarzonej z narzędziem.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CUserTool::LoadDefaulticon](#loaddefaulticon)|Ładuje domyślną ikonę dla narzędzia użytkownika.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty wiersza polecenia dla narzędzia użytkownika.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Początkowy katalog narzędzia użytkownika.|
|[CUserTool::m_strLabel](#m_strlabel)|Nazwa narzędzia wyświetlana w elemencie menu narzędzia.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat włączania narzędzi użytkownika w aplikacji, zobacz [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CUserToolsManager` utworzyć narzędzie `m_strLabel` z obiektu, ustawić zmienną elementu członkowskiego i ustawić aplikację uruchamianą przez narzędzie użytkownika. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cusertool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertool.h

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a>CUserTool::CopyIconToClipboard

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a>CUserTool::DrawToolIcon

Rysuje ikonę narzędzia użytkownika na środku określonego prostokąta.

```cpp
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*rectImage*<br/>
[w] Określa współrzędne obszaru, który ma być wyświetlany.

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a>CUserTool::GetCommand

Zwraca ciąg zawierający tekst polecenia skojarzonego z narzędziem użytkownika.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiektu zawierającego tekst polecenia skojarzonego z narzędziem użytkownika.

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a>CUserTool::GetCommandId

Zwraca identyfikator polecenia narzędzia użytkownika.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia tego narzędzia użytkownika.

## <a name="cusertoolinvoke"></a><a name="invoke"></a>CUserTool::Wywołaj

Wykonuje polecenie skojarzone z narzędziem użytkownika.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli polecenie zostało wykonane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołuje [ShellExecute,](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) aby wykonać polecenie skojarzone z narzędziem użytkownika. Funkcja kończy się niepowodzeniem, jeśli polecenie jest puste lub jeśli [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) nie powiedzie się.

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a>CUserTool::LoadDefaulticon

Ładuje domyślną ikonę dla narzędzia użytkownika.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do załadowanej ikony (HICON) lub NULL, jeśli nie można załadować domyślnej ikony.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy nie można załadować ikonę dla narzędzia zdefiniowanego przez użytkownika z pliku wykonywalnego narzędzia.

Zastąd w tej metodzie należy podać własną domyślną ikonę narzędzia.

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a>CUserTool::m_strArguments

Argumenty wiersza polecenia dla narzędzia użytkownika.

```
CString m_strArguments;
```

### <a name="remarks"></a>Uwagi

Ten ciąg jest przekazywany do narzędzia podczas wywoływania [CUserTool::Invoke](#invoke) lub gdy użytkownik kliknie polecenie skojarzone z tym narzędziem.

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a>CUserTool::m_strInitialDirectory

Określa katalog początkowy narzędzia użytkownika.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Uwagi

Ta zmienna określa katalog początkowy, który narzędzie wykonuje podczas wywoływania [CUserTool::Invoke](#invoke) lub gdy użytkownik kliknie polecenie skojarzone z tym narzędziem.

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a>CUserTool::m_strLabel

Etykieta wyświetlana w elemencie menu narzędzia.

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a>CUserTool::Serialize

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

[w] *ar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a>CUserTool::SetCommand

Ustawia aplikację uruchamiaą narzędzie użytkownika.

```cpp
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parametry

*lpszCmd*<br/>
[w] Określa nową aplikację, która ma być skojarzona z narzędziem użytkownika.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby ustawić nową aplikację, która jest uruchamiana przez narzędzie użytkownika. Metoda niszczy starą ikonę i ładuje nową ikonę z danej aplikacji. Jeśli nie można załadować ikony z aplikacji, ładuje domyślną ikonę dla narzędzia użytkownika, wywołując [CUserTool::LoadDefaultIcon](#loaddefaulticon).

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a>CUserTool::SetToolIcon

Ładuje ikonę dla narzędzia użytkownika z aplikacji używanej przez narzędzie.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt do załadowanej ikony.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby załadować ikonę, która ma być wyświetlana w elemencie menu. Ta metoda wyszukuje ikonę w pliku wykonywalnym, którego używa narzędzie. Jeśli nie ma domyślnej ikony, ikona podana przez [CUserTool::LoadDefaultIcon](#loaddefaulticon) jest używany zamiast.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Klasa CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
