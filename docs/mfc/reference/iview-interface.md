---
title: Interfejs IView
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420821"
---
# <a name="iview-interface"></a>Interfejs IView

Implementuje kilka metod, których [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień o widoku do zarządzanej kontrolki.

## <a name="syntax"></a>Składnia

```
interface class IView
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Widok IView:: OnActivateView](#onactivateview)|Wywoływane przez MFC, gdy widok jest aktywowany lub dezaktywowany.|
|[Widok IView:: OnInitialUpdate](#oninitialupdate)|Wywoływane przez platformę po pierwszym dołączeniu widoku do dokumentu, ale zanim widok jest początkowo wyświetlany.|
|[Widok IView:: OnUpdate](#onupdate)|Wywoływane przez MFC po zmodyfikowaniu dokumentu widoku; Ta funkcja umożliwia zaktualizowanie wyświetlania widoku w celu odzwierciedlenia zmian.|

## <a name="remarks"></a>Uwagi

`IView` implementuje kilka metod, których `CWinFormsView` używa do przesyłania dalej typowych powiadomień o widoku do hostowanej kontroli zarządzanej. Są to [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) i [OnActivateView](#onactivateview).

`IView` jest podobny do [CView](../../mfc/reference/cview-class.md), ale jest używany tylko z zarządzanymi widokami i kontrolkami.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Wymagania

Nagłówek: afxwinforms. h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a>Widok IView:: OnActivateView

Wywoływane przez MFC, gdy widok jest aktywowany lub dezaktywowany.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parametry

*aktywuj*<br/>
Wskazuje, czy widok jest aktywowany, czy dezaktywowany.

## <a name="oninitialupdate"></a>Widok IView:: OnInitialUpdate

Wywoływane przez platformę po pierwszym dołączeniu widoku do dokumentu, ale zanim widok jest początkowo wyświetlany.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>Widok IView:: OnUpdate

Wywoływane przez MFC po zmodyfikowaniu dokumentu widoku.
```
void OnUpdate();
```

## <a name="remarks"></a>Uwagi

Ta funkcja umożliwia zaktualizowanie wyświetlania widoku w celu odzwierciedlenia zmian.

## <a name="see-also"></a>Zobacz też

[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)
