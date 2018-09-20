---
title: Klasa CCachedDataPathProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c22d905e50c6811c82ee54d6ec08c57ef3f41182
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382833"
---
# <a name="ccacheddatapathproperty-class"></a>Klasa CCachedDataPathProperty

Implementuje OLE konntrolki przeniesionej asynchronicznie i buforowanej w pliku pamięci.

## <a name="syntax"></a>Składnia

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Konstruuje `CCachedDataPathProperty` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` obiekt, w którym do buforowania danych.|

## <a name="remarks"></a>Uwagi

Plik pamięci są przechowywane w pamięci RAM, a nie na dysku i jest przydatne w przypadku transferów szybko tymczasowych.

Wraz z `CAysncMonikerFile` i `CDataPathProperty`, `CCachedDataPathProperty` zapewnia funkcje do użytku z monikerów asynchronicznych w formantów OLE. Za pomocą `CCachedDataPathProperty` obiektów, masz możliwość asynchronicznie przesyłać dane ze źródła adres URL lub plik i zapisz go w pliku pamięci za pomocą `m_Cache` publiczną zmienną. Wszystkie dane są przechowywane w pliku pamięci i nie ma potrzeby zastąpić [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) chyba że chcesz poszukaj powiadomień i reagować. Na przykład w przypadku przenoszenia dużych. Obraz GIF, aby powiadamiać formantu, że większej ilości danych jest już dostępna, a jej powinien automatyczne odświeżenie, należy zastąpić `OnDataAvailable` się powiadomienie.

Klasa `CCachedDataPathProperty` jest tworzony na podstawie `CDataPathProperty`.

Aby uzyskać więcej informacji o sposobie używania formantów ActiveX i monikerów asynchronicznych w aplikacjach internetowych zobacz następujące tematy:

- [Internecie pierwsze kroki: Kontrolki ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Internecie pierwsze kroki: Monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

Konstruuje `CCachedDataPathProperty` obiektu.

```
CCachedDataPathProperty(COleControl* pControl = NULL);


CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Wskaźnik do obiektu formantu ActiveX, który ma zostać skojarzony z tym `CCachedDataPathProperty` obiektu.

*lpszPath*<br/>
Ścieżki, która może być bezwzględny lub względny, używane do tworzenia asynchronicznego moniker, odwołujący się do rzeczywistego lokalizacja bezwzględna właściwości. `CCachedDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CCachedDataPathProperty` obiektu dla pliku, dołączana file:// do ścieżki.

### <a name="remarks"></a>Uwagi

`COleControl` Obiekt wskazywany przez *pControl* jest używany przez [Otwórz](../../mfc/reference/cdatapathproperty-class.md#open) i pobrany przez klasy pochodne. Jeśli *pControl* ma wartość NULL, kontroli używane z `Open` powinna być ustawiona za pomocą [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Jeśli *lpszPath* ma wartość NULL, można przekazać w ścieżce za pomocą `Open` lub ustaw go za pomocą [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

Zawiera nazwę klasy w pliku pamięci, do którego dane są buforowane.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Uwagi

Plik pamięci są przechowywane w pamięci RAM, a nie na dysku.

## <a name="see-also"></a>Zobacz też

[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
