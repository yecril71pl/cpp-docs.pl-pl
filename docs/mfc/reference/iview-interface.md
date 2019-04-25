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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321952"
---
# <a name="iview-interface"></a>Interfejs IView

Implementuje kilka metod, które [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień w widoku do zarządzanego formantu.

## <a name="syntax"></a>Składnia

```
interface class IView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Metoda wywoływana przez MFC, gdy widok jest aktywowane lub dezaktywowane.|
|[IView::OnInitialUpdate](#oninitialupdate)|Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.|
|[IView::OnUpdate](#onupdate)|Metoda wywoływana przez MFC po widoku dokument został zmodyfikowany; Ta funkcja umożliwia widok, aby zaktualizować jego ekranu, aby odzwierciedlić zmiany.|

## <a name="remarks"></a>Uwagi

`IView` implementuje kilka metod, które `CWinFormsView` używa do przekazywania wspólnych powiadomień widoku do hostowanej zarządzanego formantu. Są to [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) i [OnActivateView](#onactivateview).

`IView` jest podobny do [CView](../../mfc/reference/cview-class.md), ale jest używany tylko z zarządzanych widoków i kontrolek.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Wymagania

Nagłówek: afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a> IView::OnActivateView

Metoda wywoływana przez MFC, gdy widok jest aktywowane lub dezaktywowane.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parametry

*Aktywuj*<br/>
Wskazuje, czy widok jest aktywowane lub dezaktywowane.

## <a name="oninitialupdate"></a> IView::OnInitialUpdate

Wywoływane przez platformę po widoku najpierw jest dołączony do dokumentu, ale przed wyświetleniu widoku.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate

Metoda wywoływana przez MFC po zmodyfikowaniu tego widoku dokumentu.
```
void OnUpdate();
```

## <a name="remarks"></a>Uwagi

Ta funkcja umożliwia widok, aby zaktualizować jego ekranu, aby odzwierciedlić zmiany.

## <a name="see-also"></a>Zobacz także

[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)
