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
ms.openlocfilehash: 5bb0ae073b722c97e8e30158f8f7832fd88b2fbc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779043"
---
# <a name="cusertool-class"></a>Klasa CUserTool

Narzędzie użytkownika jest element menu, który uruchamia aplikację zewnętrzną. **Narzędzia** karcie **Dostosuj** okno dialogowe ( [klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umożliwia użytkownikowi dodawanie narzędzi użytkownika i określ nazwę, poleceń, argumentów i początkowy katalog dla każdego z narzędzi użytkownika.

## <a name="syntax"></a>Składnia

```
class CUserTool : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Rysuje ikony narzędzie użytkownika w określonym prostokąta.|
|[CUserTool::GetCommand](#getcommand)|Zwraca ciąg zawierający tekst polecenia skojarzonego z narzędziem użytkownika.|
|[CUserTool::GetCommandId](#getcommandid)|Zwraca identyfikator polecenia elementu menu Narzędzia użytkownika.|
|[CUserTool::Invoke](#invoke)|Wykonuje polecenie skojarzone z narzędzia użytkownika.|
|[CUserTool::Serialize](#serialize)|Odczytuje lub zapisuje ten obiekt z lub do archiwum. (Przesłania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Określa polecenie skojarzone z narzędzia użytkownika.|
|[CUserTool::SetToolIcon](#settoolicon)|Ładuje ikonę narzędzia użytkownika z aplikacji skojarzonej z narzędziem.|

### <a name="protected-methods"></a>Metody chronione

|Name|Opis|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Ładuje domyślną ikonę narzędzie użytkownika.|

### <a name="data-members"></a>Elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty wiersza polecenia dla narzędzia użytkownika.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Początkowy katalog narzędzia użytkownika.|
|[CUserTool::m_strLabel](#m_strlabel)|Nazwa narzędzia, która jest wyświetlana w elemencie menu Narzędzia.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o sposobie włączania narzędzi użytkownika w aplikacji, zobacz [klasa CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób tworzenia narzędzia z `CUserToolsManager` obiektu, należy ustawić `m_strLabel` zmiennej składowej, a następnie ustaw aplikację, która działa narzędzie użytkownika. Ten fragment kodu jest częścią [Visual Studio przykład](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxusertool.h

##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon

Rysuje ikony narzędzie użytkownika w Centrum prostokąt określony.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*rectImage*<br/>
[in] Określa współrzędne obszaru, aby wyświetlić ikonę.

##  <a name="getcommand"></a>  CUserTool::GetCommand

Zwraca ciąg zawierający tekst polecenia skojarzonego z narzędziem użytkownika.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CString` obiekt zawierający tekst polecenia skojarzonego z narzędziem użytkownika.

##  <a name="getcommandid"></a>  CUserTool::GetCommandId

Zwraca identyfikator polecenia narzędzia użytkownika.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia to narzędzie użytkownika.

##  <a name="invoke"></a>  CUserTool::Invoke

Wykonuje polecenie skojarzone z narzędzia użytkownika.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli polecenie zostało wykonane pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołania [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) wykonanie polecenia skojarzonego z narzędziem użytkownika. Funkcja kończy się niepowodzeniem, jeśli polecenie jest puste lub jeśli [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) zakończy się niepowodzeniem.

##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon

Ładuje domyślną ikonę narzędzie użytkownika.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do załadowanych ikony (HICON), lub wartość NULL, jeśli nie można załadować ikona domyślna.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy nie można załadować ikony narzędzia zdefiniowanego przez użytkownika z pliku wykonywalnego narzędzia.

Zastępuje tę metodę, aby podać własne domyślną ikonę narzędzia.

##  <a name="m_strarguments"></a>  CUserTool::m_strArguments

Argumenty wiersza polecenia dla narzędzia użytkownika.

```
CString m_strArguments;
```

### <a name="remarks"></a>Uwagi

Ten ciąg jest przekazywany do narzędzia, gdy wywołujesz [CUserTool::Invoke](#invoke) lub kiedy użytkownik kliknie polecenie skojarzone z tym narzędziem.

##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory

Określa katalog początkowy dla narzędzia użytkownika.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Uwagi

Ta zmienna Określa katalog początkowy, który to narzędzie wykonuje podczas wywoływania [CUserTool::Invoke](#invoke) lub kiedy użytkownik kliknie polecenie skojarzone z tym narzędziem.

##  <a name="m_strlabel"></a>  CUserTool::m_strLabel

Etykieta jest wyświetlana w elemencie menu Narzędzia.

```
CString m_strLabel;
```

##  <a name="serialize"></a>  CUserTool::Serialize

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

[in] *ar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setcommand"></a>  CUserTool::SetCommand

Ustawienie aplikacji, która uruchamia narzędzie użytkownika.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Parametry

*lpszCmd*<br/>
[in] Określa nową aplikację, która ma zostać skojarzony z narzędzia użytkownika.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ustawić nową aplikację, która uruchamia narzędzie użytkownika. Metoda niszczy stare ikonę i ładuje nową ikonę z danej aplikacji. Jeśli go nie można załadować ikony z aplikacji, ładuje domyślną ikonę narzędzie użytkownika, wywołując [CUserTool::LoadDefaultIcon](#loaddefaulticon).

##  <a name="settoolicon"></a>  CUserTool::SetToolIcon

Ładuje ikonę narzędzia użytkownika z aplikacji, która korzysta z narzędzia.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Wartość zwracana

Dojście do ikony załadowane.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby załadować ikony, które mają być wyświetlane dla elementu menu. Metoda ta wyszukuje ikony w pliku wykonywalnego, który korzysta z narzędzia. Jeśli nie ma ikona domyślna, ikona udostępniane przez [CUserTool::LoadDefaultIcon](#loaddefaulticon) zamian jest używana.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Klasa CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
