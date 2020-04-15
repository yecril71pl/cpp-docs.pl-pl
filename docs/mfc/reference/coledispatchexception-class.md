---
title: Klasa COleDispatchException
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375060"
---
# <a name="coledispatchexception-class"></a>Klasa COleDispatchException

Obsługuje wyjątki specyficzne dla `IDispatch` interfejsu OLE, który jest kluczową częścią automatyzacji OLE.

## <a name="syntax"></a>Składnia

```
class COleDispatchException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Kontekst pomocy dla błędu.|
|[COleDispatchException::m_strDescription](#m_strdescription)|Opis błędu werbalnego.|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Plik Pomocy do `m_dwHelpContext`użycia z plikiem .|
|[COleDispatchException::m_strSource](#m_strsource)|Aplikacja, która wygenerowała wyjątek.|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-specyficzny kod błędu.|

## <a name="remarks"></a>Uwagi

Podobnie jak inne klasy wyjątków pochodzące z klasy `CException` podstawowej, `COleDispatchException` mogą być używane z makrami THROW, THROW_LAST, TRY, CATCH, AND_CATCH i END_CATCH.

Ogólnie rzecz biorąc należy wywołać [AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception) do tworzenia i rzucania `COleDispatchException` obiektu.

Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuły [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: Wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext

Identyfikuje kontekst pomocy w pomocy aplikacji (. HLP).

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest ustawiany przez funkcję [AfxThrowOleDispatchException,](exception-processing.md#afxthrowoledispatchexception) gdy zostanie zgłoszony wyjątek.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatchException::m_strDescription

Zawiera opis błędu słownego, na przykład "Dysk pełny".

```
CString m_strDescription;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest ustawiany przez funkcję [AfxThrowOleDispatchException,](exception-processing.md#afxthrowoledispatchexception) gdy zostanie zgłoszony wyjątek.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile

Struktura wypełnia ten ciąg nazwą pliku pomocy aplikacji.

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatchException::m_strSource

Struktura wypełnia ten ciąg o nazwie aplikacji, która wygenerowała wyjątek.

```
CString m_strSource;
```

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatchException::m_wCode

Zawiera kod błędu specyficzny dla aplikacji.

```
WORD m_wCode;
```

### <a name="remarks"></a>Uwagi

Ten element członkowski jest ustawiany przez funkcję [AfxThrowOleDispatchException,](exception-processing.md#afxthrowoledispatchexception) gdy zostanie zgłoszony wyjątek.

## <a name="see-also"></a>Zobacz też

[Próbka MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)<br/>
[Klasa COleException](../../mfc/reference/coleexception-class.md)
