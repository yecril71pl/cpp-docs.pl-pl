---
title: CHtmlEditDoc Class
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: f468de46cf6d8a8bfcd60521df8b1076a98f0735
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285337"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc Class

Za pomocą [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), zapewnia funkcję platformy edycji WebBrowser w kontekście architektury widoku dokumentu MFC.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Konstruuje `CHtmlEditDoc` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Pobiera `CHtmlEditView` obiekt dołączony do tego dokumentu.|
|[CHtmlEditDoc::IsModified](#ismodified)|Zwraca, czy formant WebBrowser skojarzony widok zawiera dokument, który został zmodyfikowany przez użytkownika.|
|[CHtmlEditDoc::OpenURL](#openurl)|Zostanie otwarty adres URL.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

Konstruuje `CHtmlEditDoc` obiektu.

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

Pobiera [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) obiekt dołączony do tego dokumentu.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do dokumentu `CHtmlEditView` obiektu.

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

Zwraca, czy formant WebBrowser skojarzony widok zawiera dokument, który został zmodyfikowany przez użytkownika.

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

Zostanie otwarty adres URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Adres URL do otwarcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

## <a name="see-also"></a>Zobacz także

[Przykładowe HTMLEdit](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
