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
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751282"
---
# <a name="iview-interface"></a>Interfejs IView

Implementuje kilka metod, które [CWinFormsView](../../mfc/reference/cwinformsview-class.md) używa do wysyłania powiadomień widoku do formantu zarządzanego.

## <a name="syntax"></a>Składnia

```
interface class IView
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Wywoływane przez MFC, gdy widok jest aktywowany lub dezaktywowany.|
|[IView::OnInitialUpdate](#oninitialupdate)|Wywoływane przez ramy po widoku jest najpierw dołączony do dokumentu, ale przed widok jest początkowo wyświetlany.|
|[IView::OnUpdate](#onupdate)|Wywoływane przez MFC po zmodyfikowaniu dokumentu widoku; ta funkcja umożliwia widokowi aktualizację jego wyświetlania w celu odzwierciedlenia modyfikacji.|

## <a name="remarks"></a>Uwagi

`IView`implementuje kilka `CWinFormsView` metod, które służy do przekazywania powiadomień widoku wspólnego do hostowanego formantu zarządzanego. Są to [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) i [OnActivateView](#onactivateview).

`IView`jest podobny do [CView](../../mfc/reference/cview-class.md), ale jest używany tylko z zarządzanych widoków i formantów.

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Wymagania

Nagłówek: afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView

Wywoływane przez MFC, gdy widok jest aktywowany lub dezaktywowany.

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parametry

*aktywuj*<br/>
Wskazuje, czy widok jest aktywowany, czy dezaktywowany.

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate

Wywoływane przez ramy po widoku jest najpierw dołączony do dokumentu, ale przed widok jest początkowo wyświetlany.

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate

Wywoływane przez MFC po zmodyfikowaniu dokumentu widoku.

```cpp
void OnUpdate();
```

## <a name="remarks"></a>Uwagi

Ta funkcja umożliwia widok, aby zaktualizować jego wyświetlacz, aby odzwierciedlić modyfikacje.

## <a name="see-also"></a>Zobacz też

[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)
