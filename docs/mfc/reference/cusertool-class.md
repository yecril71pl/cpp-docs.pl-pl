---
title: Klasa CUserTool | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59f5ab622d6124e830028ea61a0c77583f76d015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374756"
---
# <a name="cusertool-class"></a>Klasa CUserTool
Narzędzie użytkownika jest element menu uruchomionym aplikacji zewnętrznej. **Narzędzia** na karcie **Dostosuj** okno dialogowe ( [CMFCToolBarsCustomizeDialog klasy](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) umożliwia użytkownikowi, aby dodać użytkownika narzędzia i określ nazwę, argumentów i początkowy katalog dla każdego użytkownika narzędzia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|Rysuje ikonę narzędzie użytkownika w prostokącie określonego.|  
|[CUserTool::GetCommand](#getcommand)|Zwraca ciąg zawierający tekst polecenie skojarzone z narzędzia użytkownika.|  
|[CUserTool::GetCommandId](#getcommandid)|Zwraca identyfikator polecenia elementu menu Narzędzia użytkownika.|  
|[CUserTool::Invoke](#invoke)|Wykonuje polecenie skojarzone z narzędzia użytkownika.|  
|[CUserTool::Serialize](#serialize)|Odczytuje i zapisuje ten obiekt z lub do archiwum. (Przesłania [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CUserTool::SetCommand](#setcommand)|Ustawia polecenie skojarzone z narzędzia użytkownika.|  
|[CUserTool::SetToolIcon](#settoolicon)|Ładuje ikonę narzędzia użytkownika z aplikacji skojarzonej z narzędziem.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Ładuje domyślną ikonę narzędzie użytkownika.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|Argumenty wiersza polecenia dla narzędzia użytkownika.|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Początkowy katalog dla narzędzia użytkownika.|  
|[CUserTool::m_strLabel](#m_strlabel)|Nazwa narzędzia, która jest wyświetlana w elemencie menu Narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o sposobie włączania narzędzi użytkownika w aplikacji, zobacz [CUserToolsManager klasy](../../mfc/reference/cusertoolsmanager-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak utworzyć narzędzie z `CUserToolsManager` obiekt, ustaw `m_strLabel` zmiennej członkowskiej i zestaw aplikacji, która uruchamia narzędzie do użytkowników. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon  
 Rysuje ikonę narzędzie użytkownika w Centrum prostokąt określony.  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rectImage`  
 Określa współrzędne obszaru, aby wyświetlić ikonę.  
  
##  <a name="getcommand"></a>  CUserTool::GetCommand  
 Zwraca ciąg zawierający tekst polecenie skojarzone z narzędzia użytkownika.  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do `CString` obiekt, który zawiera tekst polecenie skojarzone z narzędzia użytkownika.  
  
##  <a name="getcommandid"></a>  CUserTool::GetCommandId  
 Zwraca identyfikator polecenia narzędzia użytkownika.  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia narzędzia użytkownika.  
  
##  <a name="invoke"></a>  CUserTool::Invoke  
 Wykonuje polecenie skojarzone z narzędzia użytkownika.  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli polecenie zostało wykonane pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) do wykonania polecenia skojarzonego z narzędziem użytkownika. Funkcja zakończy się niepowodzeniem, jeśli polecenie jest puste lub jeśli [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) zakończy się niepowodzeniem.  
  
##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon  
 Ładuje domyślną ikonę narzędzie użytkownika.  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do ikony załadować ( `HICON`), lub `NULL` Jeśli ikona domyślna nie może zostać załadowany.  
  
### <a name="remarks"></a>Uwagi  
 Platformę wywołuje tę metodę, gdy nie można załadować z pliku wykonywalnego narzędzia ikony narzędzia zdefiniowane przez użytkownika.  
  
 Przesłonić tę metodę, aby podać własne narzędzia domyślną ikonę.  
  
##  <a name="m_strarguments"></a>  CUserTool::m_strArguments  
 Argumenty wiersza polecenia dla narzędzia użytkownika.  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten ciąg jest przekazywany do narzędzia podczas wywoływania [CUserTool::Invoke](#invoke) lub gdy użytkownik klika polecenie skojarzone z tym narzędziem.  
  
##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory  
 Określa katalog początkowy dla narzędzia użytkownika.  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta zmienna Określa początkowy katalog, w którym narzędzie jest wykonywana w przypadku wywołania [CUserTool::Invoke](#invoke) lub gdy użytkownik klika polecenie skojarzone z tym narzędziem.  
  
##  <a name="m_strlabel"></a>  CUserTool::m_strLabel  
 Etykiety, dla której jest wyświetlany w elemencie menu Narzędzia.  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>  CUserTool::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `ar`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcommand"></a>  CUserTool::SetCommand  
 Ustawia aplikacji, która uruchamia narzędzie do użytkowników.  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszCmd`  
 Określa nową aplikację do skojarzenia z narzędzia użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby ustawić nową aplikację, która uruchamia narzędzie do użytkowników. Metoda niszczy ikonę stary i ładuje nową ikonę z danej aplikacji. Jeśli ikona nie może załadować z aplikacji, wywołując ładuje domyślną ikonę narzędzie użytkownika [CUserTool::LoadDefaultIcon](#loaddefaulticon).  
  
##  <a name="settoolicon"></a>  CUserTool::SetToolIcon  
 Ładuje ikonę narzędzia użytkownika z aplikacji, która używa narzędzia.  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do ikony załadowany.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby załadować ikony, który będzie wyświetlany na elemencie menu. Ta metoda umożliwia wyszukiwanie ikonę programu w pliku wykonywalnego, który korzysta z narzędzia. Jeśli nie ma domyślnej ikony, ikona udostępniane przez [CUserTool::LoadDefaultIcon](#loaddefaulticon) zamiast niego jest używana.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Klasa CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
