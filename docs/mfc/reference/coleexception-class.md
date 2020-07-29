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
ms.openlocfilehash: c82099d816bc8ee8c179e9d4656f474156a629a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233200"
---
# <a name="coleexception-class"></a>Klasa COleException

Reprezentuje warunek wyjątku związany z operacją OLE.

## <a name="syntax"></a>Składnia

```
class COleException : public CException
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleException::P procesu](#process)|Tłumaczy przechwycony wyjątek na kod powrotu OLE.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[COleException:: m_sc](#m_sc)|Zawiera kod stanu, który wskazuje przyczynę wyjątku.|

## <a name="remarks"></a>Uwagi

`COleException`Klasa zawiera publiczny element członkowski danych, który przechowuje kod stanu wskazujący przyczynę wyjątku.

Ogólnie rzecz biorąc nie należy tworzyć `COleException` obiektu bezpośrednio; zamiast tego należy wywołać [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Aby uzyskać więcej informacji o wyjątkach, zobacz [Obsługa wyjątków artykułów (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COleException:: m_sc

Ten element członkowski danych przechowuje kod stanu OLE, który wskazuje przyczynę wyjątku.

```
SCODE m_sc;
```

### <a name="remarks"></a>Uwagi

Wartość tej zmiennej jest ustawiana przez [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Aby uzyskać więcej informacji na temat SCODE, zobacz [strukturę kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COleException::P procesu

Wywołaj funkcję elementu członkowskiego **procesu** , aby przetłumaczyć przechwycony wyjątek na kod stanu OLE.

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>Parametry

*pAnyException*<br/>
Wskaźnik na przechwycony wyjątek.

### <a name="return-value"></a>Wartość zwracana

Kod stanu OLE.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Ta funkcja jest **`static`** .

Aby uzyskać więcej informacji na temat SCODE, zobacz [strukturę kodów błędów modelu COM](/windows/win32/com/structure-of-com-error-codes) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [COleDispatchDriver::](../../mfc/reference/coledispatchdriver-class.md#createdispatch)...

## <a name="see-also"></a>Zobacz także

[Przykład CALCDRIV MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CException](../../mfc/reference/cexception-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
