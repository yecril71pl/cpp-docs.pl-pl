---
title: Klasa CMFCDesktopAlertWndInfo
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367590"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>Klasa CMFCDesktopAlertWndInfo

Klasa `CMFCDesktopAlertWndInfo` jest używana z [CMFCDesktopAlertWnd Klasy](../../mfc/reference/cmfcdesktopalertwnd-class.md). Określa formanty, które są wyświetlane, jeśli pojawi się okno alertu pulpitu.

## <a name="syntax"></a>Składnia

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operator=](#operator_eq)||

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Uchwyt do wyświetlanej ikony.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|Identyfikator polecenia skojarzony z łączem w oknie alertu pulpitu.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Tekst wyświetlany w oknie alertu na pulpicie.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Łącze wyświetlane w oknie alertu na pulpicie.|

## <a name="remarks"></a>Uwagi

Klasa `CMFCDesktopAlertWndInfo` jest przekazywana do [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metody, aby określić elementy, które są wyświetlane w domyślnym oknie dialogowym okna alertu pulpitu. Domyślne okno dialogowe może zawierać trzy elementy:

- Ikona, która jest ustawiona przez wywołanie [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Etykieta lub wiadomość tekstowa, która jest ustawiana przez wywołanie [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Łącze, które jest ustawiane przez wywołanie [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Aby ustawić polecenie wykonywane po kliknięciu łącza, zadzwoń do [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Jeśli domyślne okno dialogowe nie jest wystarczające, można utworzyć niestandardowe okno dialogowe i przekazać je do [metody CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) zamiast tej klasy. Aby uzyskać więcej informacji, zobacz [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCDesktopAlertWndInfo` używać różnych elementów członkowskich w klasie. W przykładzie pokazano, jak ustawić uchwyt na ikonę, która jest wyświetlana, tekst wyświetlany w oknie alertu pulpitu, łącze wyświetlane w oknie alertu pulpitu i identyfikator polecenia skojarzony z łączem w oknie alertu na pulpicie. W tym przykładzie jest częścią [przykładu demo alertów pulpitu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operator=

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parametry

[w] *src ( src )*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon

Uchwyt do wyświetlanej ikony.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID

Identyfikator polecenia skojarzony z łączem w oknie alertu pulpitu.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Uwagi

Identyfikator polecenia jest wysyłany do właściciela okna podręcznego, gdy użytkownik kliknie łącze określone przez [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText

Tekst wyświetlany w oknie alertu na pulpicie.

```
CString m_strText;
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL

Łącze wyświetlane w oknie alertu na pulpicie.

```
CString m_strURL;
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik kliknie łącze, polecenie, które ma IDENTYFIKATOR POLECENIA [CMFCDesktopAlertWndInfo::m_nURLCmdID,](#m_nurlcmdid) zostanie wysłane do właściciela okna podręcznego.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Tworzenie](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
