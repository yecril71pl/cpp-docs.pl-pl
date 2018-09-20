---
title: Klasa COleDispatchException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs:
- C++
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b921f03f965e02b85ebc7bd9efff45910ab6adfb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431076"
---
# <a name="coledispatchexception-class"></a>Klasa COleDispatchException

Wyjątki uchwytów specyficzne OLE `IDispatch` interfejs, który jest kluczową częścią automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleDispatchException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Kontekst Pomoc dla błędu.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Opis błędu słownej.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Plik do korzystania z pomocy `m_dwHelpContext`.|
|[COleDispatchException::m_strSource](#m_strsource)|Aplikacja, która wygenerowała wyjątek.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-określonego kodu błędu.|

## <a name="remarks"></a>Uwagi

Jak pochodną klasy wyjątków `CException` podstawowej klasy, `COleDispatchException` mogą być używane z THROW, THROW_LAST, TRY, CATCH, AND_CATCH i END_CATCH makra.

Ogólnie rzecz biorąc, należy wywołać [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) do tworzenia i zgłosić `COleDispatchException` obiektu.

Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext

Identyfikuje kontekstu pomocy w aplikacji pomocy (. Plik HLP).

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest ustawiany przez funkcję [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) kiedy zgłaszany jest wyjątek.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription

Zawiera opis błędu werbalne, takie jak "Dysk jest zapełniony."

```
CString m_strDescription;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest ustawiany przez funkcję [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) kiedy zgłaszany jest wyjątek.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile

Struktura wypełnia tego ciągu o nazwie pliku pomocy w aplikacji.

```
CString m_strHelpFile;
```

##  <a name="m_strsource"></a>  COleDispatchException::m_strSource

Struktura wypełnia tego ciągu o nazwie aplikacji, który wygenerował wyjątek.

```
CString m_strSource;
```

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

##  <a name="m_wcode"></a>  COleDispatchException::m_wCode

Zawiera kod błędu określony dla twojej aplikacji.

```
WORD m_wCode;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest ustawiany przez funkcję [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) kiedy zgłaszany jest wyjątek.

## <a name="see-also"></a>Zobacz też

[Próbki MFC CALCDRIV](../../visual-cpp-samples.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)<br/>
[Klasa COleException](../../mfc/reference/coleexception-class.md)
