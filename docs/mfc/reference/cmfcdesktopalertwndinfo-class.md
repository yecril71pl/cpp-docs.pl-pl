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
ms.openlocfilehash: a4b3d8769b3d267c0bd3f81269dd3b8ab3cf3184
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403649"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>Klasa CMFCDesktopAlertWndInfo

`CMFCDesktopAlertWndInfo` Klasa jest używana z [klasa CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md). Określa formanty, które są wyświetlane, gdy pojawi się okno alertu pulpitu.

## <a name="syntax"></a>Składnia

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Dojście do ikony, która jest wyświetlana.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|Identyfikator polecenia skojarzony z linkiem na okno alertu pulpitu.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Tekst, który jest wyświetlany na okno alertu pulpitu.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Link, który jest wyświetlany na okno alertu pulpitu.|

## <a name="remarks"></a>Uwagi

`CMFCDesktopAlertWndInfo` Klasy jest przekazywany do [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metodę, aby określić elementy, które są wyświetlane w oknie dialogowym domyślne programu okno alertu pulpitu. Okno dialogowe domyślne może zawierać trzy elementy:

- Ikona, która została ustawiona przez wywołanie metody [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Etykiety lub wiadomości SMS, która została ustawiona przez wywołanie metody [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Łącze, która została ustawiona przez wywołanie metody [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Aby ustawić polecenia, który jest wykonywany po kliknięciu łącza, należy wywołać [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Gdy okno dialogowe domyślne nie są wystarczające, można utworzyć niestandardowe okno dialogowe i przekazać go do [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metody zamiast korzystać z tej klasy. Aby uzyskać więcej informacji, zobacz [klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać różnych członków w `CMFCDesktopAlertWndInfo` klasy. W przykładzie pokazano, jak ustawić dojście do ikonę, która jest wyświetlana, tekst, który jest wyświetlany na okno alertu pulpitu, łącza, który jest wyświetlany na okno alertu pulpitu i identyfikator polecenia, który jest skojarzony z linkiem na okno alertu pulpitu. W tym przykładzie jest częścią [próbka Demo alertu pulpitu](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxDesktopAlertDialog.h

##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator =

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parametry

[in] *src*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon

Dojście do ikony, która jest wyświetlana.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID

Identyfikator polecenia skojarzony z linkiem na okno alertu pulpitu.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Uwagi

Identyfikator polecenia jest wysyłany do właściciela okna podręcznego, gdy użytkownik kliknie link, określony przez [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText

Tekst, który jest wyświetlany na okno alertu pulpitu.

```
CString m_strText;
```

### <a name="remarks"></a>Uwagi

##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL

Link, który jest wyświetlany na okno alertu pulpitu.

```
CString m_strURL;
```

### <a name="remarks"></a>Uwagi

Gdy użytkownik kliknie link, polecenie zawierający [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) identyfikator polecenia zostaną wysłane do właściciela tego okna.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[Klasa CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
