---
title: Klasa CHtmlEditDoc
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
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352172"
---
# <a name="chtmleditdoc-class"></a>Klasa CHtmlEditDoc

Z [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), zapewnia funkcjonalność platformy edycji WebBrowser w kontekście architektury MFC widoku dokumentów.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Konstruuje `CHtmlEditDoc` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Pobiera `CHtmlEditView` obiekt dołączony do tego dokumentu.|
|[CHtmlEditDoc::JestModified](#ismodified)|Zwraca, czy kontrolka WebBrowser skojarzonego widoku zawiera dokument, który został zmodyfikowany przez użytkownika.|
|[CHtmlEditDoc::OpenURL](#openurl)|Otwiera adres URL.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc

Konstruuje `CHtmlEditDoc` obiekt.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtmlEditDoc::GetView

Pobiera [obiekt CHtmlEditView](../../mfc/reference/chtmleditview-class.md) dołączony do tego dokumentu.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `CHtmlEditView` obiektu dokumentu.

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc::JestModified

Zwraca, czy kontrolka WebBrowser skojarzonego widoku zawiera dokument, który został zmodyfikowany przez użytkownika.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtmlEditDoc::OpenURL

Otwiera adres URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parametry

*lpszURL*<br/>
Adres URL do otwarcia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

## <a name="see-also"></a>Zobacz też

[Przykład htmledytuj](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
