---
title: Klasa COleException
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375010"
---
# <a name="coleexception-class"></a>Klasa COleException

Reprezentuje warunek wyjątku związane z operacją OLE.

## <a name="syntax"></a>Składnia

```
class COleException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleException::Pproces](#process)|Tłumaczy przechwycony wyjątek na kod zwrotny OLE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|Zawiera kod stanu, który wskazuje przyczynę wyjątku.|

## <a name="remarks"></a>Uwagi

Klasa `COleException` zawiera element członkowski danych publicznych, który przechowuje kod stanu wskazujący przyczynę wyjątku.

Ogólnie rzecz biorąc nie `COleException` należy tworzyć obiektu bezpośrednio; zamiast tego należy zadzwonić [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuły [Obsługa wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: Wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cexception](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException::m_sc

Ten element członkowski danych przechowuje kod stanu OLE, który wskazuje przyczynę wyjątku.

```
SCODE m_sc;
```

### <a name="remarks"></a>Uwagi

Wartość tej zmiennej jest ustawiana przez [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Aby uzyskać więcej informacji na temat SCODE, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::Pproces

Wywołanie **Process** funkcji elementu członkowskiego, aby przetłumaczyć przechwycony wyjątek na kod stanu OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parametry

*pAnyException (Nieekceptiona)*<br/>
Wskaźnik do przechwyconego wyjątku.

### <a name="return-value"></a>Wartość zwracana

Kod stanu OLE.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja jest **statyczna**.

Aby uzyskać więcej informacji na temat SCODE, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).

## <a name="see-also"></a>Zobacz też

[Próbka MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
