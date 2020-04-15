---
title: Klasa CCachedDataPathProperty
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352364"
---
# <a name="ccacheddatapathproperty-class"></a>Klasa CCachedDataPathProperty

Implementuje właściwość kontroli OLE przekazywane asynchronicznie i buforowane w pliku pamięci.

## <a name="syntax"></a>Składnia

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Konstruuje `CCachedDataPathProperty` obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`obiekt, w którym mają być buforowane dane.|

## <a name="remarks"></a>Uwagi

Plik pamięci jest przechowywany w pamięci RAM, a nie na dysku i jest przydatny do szybkich transferów tymczasowych.

Wraz `CAysncMonikerFile` z `CDataPathProperty` `CCachedDataPathProperty` i , zapewnia funkcjonalność do korzystania z asynchronicznych monikers w formanty OLE. Za `CCachedDataPathProperty` pomocą obiektów można przesyłać dane asynchronicznie z adresu URL lub źródła plików `m_Cache` i przechowywać go w pliku pamięci za pośrednictwem zmiennej publicznej. Wszystkie dane są przechowywane w pliku pamięci i nie ma potrzeby zastępowania [OnDataAvailable,](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) chyba że chcesz obserwować powiadomienia i odpowiadać. Na przykład, jeśli przenosisz duży plik . GIF i chcesz powiadomić kontrolę, że więcej danych dotarło i należy `OnDataAvailable` go przerysować, zastąpić, aby dokonać powiadomienia.

Klasa `CCachedDataPathProperty` jest pochodną `CDataPathProperty`.

Aby uzyskać więcej informacji na temat używania monikerów asynchronicznych i formantów ActiveX w aplikacjach internetowych, zobacz następujące tematy:

- [Pierwsze kroki w Internecie: Formanty ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Pierwsze kroki internetowe: Asynchroniczne Monikers](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Colestreamfile](../../mfc/reference/colestreamfile-class.md)

[Plik CMoniker](../../mfc/reference/cmonikerfile-class.md)

[Casyncmonikerfile](../../mfc/reference/casyncmonikerfile-class.md)

[Cdatapathproperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty

Konstruuje `CCachedDataPathProperty` obiekt.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pKontroluj*<br/>
Wskaźnik do obiektu sterującego ActiveX, który `CCachedDataPathProperty` ma być skojarzony z tym obiektem.

*lpszPath (lpszPath)*<br/>
Ścieżka, która może być bezwzględna lub względna, używana do tworzenia asynchroniiowego monikera, który odwołuje się do rzeczywistej bezwzględnej lokalizacji właściwości. `CCachedDataPathProperty`używa adresów URL, a nie nazwy plików. Jeśli chcesz `CCachedDataPathProperty` obiekt dla pliku, należy dołączyć file:// do ścieżki.

### <a name="remarks"></a>Uwagi

Obiekt `COleControl` wskazywane przez *pControl* jest używany przez [Open](../../mfc/reference/cdatapathproperty-class.md#open) i pobierane przez klasy pochodne. Jeśli *pControl* ma wartość NULL, formant używany z `Open` należy ustawić z [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Jeśli *lpszPath* ma wartość NULL, można `Open` przejść w ścieżce lub ustawić ją za pomocą [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPathProperty::m_Cache

Zawiera nazwę klasy pliku pamięci, do którego są buforowane dane.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Uwagi

Plik pamięci jest przechowywany w pamięci RAM, a nie na dysku.

## <a name="see-also"></a>Zobacz też

[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
