---
title: Klasa COleVariant
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 66ff3d684dba6b876ae94699209a43aaf4db5f23
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916949"
---
# <a name="colevariant-class"></a>Klasa COleVariant

Hermetyzuje typ danych [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) .

## <a name="syntax"></a>Składnia

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleVariant::COleVariant](#colevariant)|Konstruuje `COleVariant` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleVariant:: Attach](#attach)|Dołącza wariant do `COleVariant`.|
|[COleVariant:: ChangeType](#changetype)|Zmienia Typ wariantu tego `COleVariant` obiektu.|
|[COleVariant:: Clear](#clear)|Czyści ten `COleVariant` obiekt.|
|[COleVariant::D etach](#detach)|Odłącza element Variant od `COleVariant` i zwraca typ Variant.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Pobiera tablicę bajtową z istniejącej tablicy wariantów.|
|[COleVariant:: SetString](#setstring)|Ustawia ciąg na określony typ, zazwyczaj ANSI.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleVariant:: operator LPCVARIANT](#operator_lpcvariant)|`COleVariant` Konwertuje wartość`LPCVARIANT`na.|
|[COleVariant:: operator LPVARIANT](#operator_lpvariant)|`COleVariant` Konwertuje obiekt`LPVARIANT`na.|
|[COleVariant:: operator =](#operator_eq)|`COleVariant` Kopiuje wartość.|
|[COleVariant:: operator = =](#operator_eq_eq)|Porównuje `COleVariant` dwie wartości.|
|[COleVariant:: operator &lt;, &lt;&gt;&gt;](#operator_lt_lt__gt_gt)|`CArchive` Wyprowadza wartość do lub`CDumpContext` i`COleVariant` wprowadza obiekt z `CArchive`. `COleVariant`|

## <a name="remarks"></a>Uwagi

Ten typ danych jest używany w automatyzacji OLE. Struktura [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams) zawiera wskaźnik do tablicy struktur wariantów. Struktura służy do przekazywania parametrów do elementu [IDispatch:: Invoke.](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) `DISPPARAMS`

> [!NOTE]
> Ta klasa jest pochodną `VARIANT` struktury. Oznacza to, że można przekazać `COleVariant` do parametru, który wywołuje `VARIANT` dla a i że elementy członkowskie `VARIANT` danych struktury są dostępnymi elementami członkowskimi `COleVariant`danych.

Dwie powiązane klasy MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) i [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) hermetyzują typy danych Variant Currency ( `VT_CY`) i Date ( `VT_DATE`). Klasa jest używana w szerokim stopniu w klasach DAO; Zobacz te klasy, aby uzyskać typowy sposób użycia tej klasy, na przykład [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md) `COleVariant`

Aby uzyskać więcej informacji, zobacz wpisy [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [Currency](/windows/desktop/api/wtypes/ns-wtypes-tagcy), [DISPPARAMS](/windows/desktop/api/oaidl/ns-oaidl-tagdispparams)i [IDispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) w Windows SDK.

Aby uzyskać więcej informacji na `COleVariant` temat klasy i jej użycia w automatyzacji OLE, zobacz "przekazywanie parametrów w automatyzacji OLE" w temacie [Automatyzacja](../../mfc/automation.md)artykułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

##  <a name="attach"></a>COleVariant:: Attach

Wywołaj tę funkcję, aby dołączyć dany obiekt [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) do bieżącego `COleVariant` obiektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Istniejący `VARIANT` obiekt do dołączenia do bieżącego `COleVariant` obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia typ VARTYPE elementu *varSrc* na VT_EMPTY.

Aby uzyskać więcej informacji, zobacz zapisy [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) i [VarEnum](/windows/desktop/api/wtypes/ne-wtypes-varenum) w Windows SDK.

##  <a name="colevariant"></a>COleVariant::COleVariant

Konstruuje `COleVariant` obiekt.

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
Istniejący `COleVariant` obiekt lub `VARIANT` , który ma zostać skopiowany do nowego `COleVariant` obiektu.

*pSrc*<br/>
Wskaźnik do `VARIANT` obiektu, który zostanie skopiowany do nowego `COleVariant` obiektu.

*lpszSrc*<br/>
Ciąg zakończony znakiem null, który ma zostać skopiowany do `COleVariant` nowego obiektu.

*vtSrc*<br/>
`VARTYPE` Dla nowego`COleVariant` obiektu.

*strSrc*<br/>
Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który ma zostać skopiowany do nowego `COleVariant` obiektu.

*nSrc*, *lSrc* wartość liczbową do skopiowania do nowego `COleVariant` obiektu.

*vtSrc*<br/>
`VARTYPE` Dla nowego`COleVariant` obiektu.

*curSrc*<br/>
Obiekt [COleCurrency](../../mfc/reference/colecurrency-class.md) , który ma zostać skopiowany do nowego `COleVariant` obiektu.

*fltSrc*, *dblSrc*<br/>
Wartość liczbowa do skopiowania do nowego `COleVariant` obiektu.

*timeSrc*<br/>
Obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) , który ma zostać skopiowany do nowego `COleVariant` obiektu.

*arrSrc*<br/>
Obiekt [CByteArray](../../mfc/reference/cbytearray-class.md) , który ma zostać skopiowany do nowego `COleVariant` obiektu.

*lbSrc*<br/>
Obiekt [CLongBinary](../../mfc/reference/clongbinary-class.md) , który ma zostać skopiowany do nowego `COleVariant` obiektu.

*pidl*<br/>
Wskaźnik do struktury [ITEMIDLIST](/windows/desktop/api/shtypes/ns-shtypes-itemidlist) , który ma zostać skopiowany do nowego `COleVariant` obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory tworzą `COleVariant` nowe obiekty zainicjowane do określonej wartości. Poniżej znajduje się krótki opis każdego z tych konstruktorów.

- **COleVariant ()** Tworzy pusty `COleVariant` obiekt VT_EMPTY.

- **COleVariant (** *varSrc* **)** Kopiuje istniejący `VARIANT` obiekt lub `COleVariant` . Typ Variant jest zachowywany.

- **COleVariant (** *pSrc* **)** Kopiuje istniejący `VARIANT` obiekt lub `COleVariant` . Typ Variant jest zachowywany.

- **COleVariant (** *lpszSrc* **)** Kopiuje ciąg do nowego obiektu, VT_BSTR (UNICODE).

- **COleVariant (** *lpszSrc* **,** *vtSrc* **)** Kopiuje ciąg do nowego obiektu. Parametr *vtSrc* musi mieć wartość VT_BSTR (Unicode) lub VT_BSTRT (ANSI).

- **COleVariant (** *strSrc* **)** Kopiuje ciąg do nowego obiektu, VT_BSTR (UNICODE).

- **COleVariant (** *nSrc* **)** Kopiuje 8-bitową liczbę całkowitą do nowego obiektu, VT_UI1.

- **COleVariant (** *nSrc* **,** *vtSrc* **)** Kopiuje 16-bitową liczbę całkowitą (lub wartość logiczną) do nowego obiektu. Parametr *vtSrc* musi mieć wartość VT_I2 lub VT_BOOL.

- **COleVariant (** *lSrc* **,** *vtSrc* **)** Kopiuje 32-bitową liczbę całkowitą (lub wartość SCODE) do nowego obiektu. Parametr *vtSrc* musi mieć wartość VT_I4, VT_ERROR lub VT_BOOL.

- **COleVariant (** *curSrc* **)** `COleCurrency` Kopiuje wartość do nowego obiektu, VT_CY.

- **COleVariant (** *fltSrc* **)** Kopiuje 32-bitową wartość zmiennoprzecinkową do nowego obiektu, VT_R4.

- **COleVariant (** *dblSrc* **)** Kopiuje 64-bitową wartość zmiennoprzecinkową do nowego obiektu, VT_R8.

- **COleVariant (** *timeSrc* **)** `COleDateTime` Kopiuje wartość do nowego obiektu, VT_DATE.

- **COleVariant (** *arrSrc* **)** `CByteArray` Kopiuje obiekt do nowego obiektu, VT_EMPTY.

- **COleVariant (** *lbSrc* **)** `CLongBinary` Kopiuje obiekt do nowego obiektu, VT_EMPTY.

Aby uzyskać więcej informacji na temat SCODE, zobacz [strukturę kodów błędów modelu COM](/windows/desktop/com/structure-of-com-error-codes) w Windows SDK.

##  <a name="changetype"></a>COleVariant:: ChangeType

Konwertuje typ wartości wariantu w tym `COleVariant` obiekcie.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*VARTYPE*<br/>
Typ VARTYPE dla tego `COleVariant` obiektu.

*pSrc*<br/>
Wskaźnik do obiektu [wariantu](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) do przekonwertowania. Jeśli ta wartość jest równa null `COleVariant` , ten obiekt jest używany jako źródło dla konwersji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz wpisy [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VarEnum](/windows/desktop/api/wtypes/ne-wtypes-varenum)i [VariantChangeType](/windows/desktop/api/oleauto/nf-oleauto-variantchangetype) w Windows SDK.

##  <a name="clear"></a>COleVariant:: Clear

`VARIANT`Czyści.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Ustawia typ VARTYPE dla tego obiektu na VT_EMPTY. `COleVariant` Destruktor wywołuje tę funkcję.

Aby uzyskać więcej informacji, zobacz `VARIANT`, VARTYPE i `VariantClear` wpisów w Windows SDK.

##  <a name="detach"></a>COleVariant::D etach

Odłącza źródłowy obiekt [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) od tego `COleVariant` obiektu.

```
VARIANT Detach();
```

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia typ VARTYPE dla tego `COleVariant` obiektu na VT_EMPTY.

> [!NOTE]
>  Po wywołaniu `Detach`, jest on odpowiedzialny za wywoływanie `VariantClear` w wyniku `VARIANT` struktury.

Aby uzyskać więcej informacji, zobacz wpisy [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VarEnum](/windows/desktop/api/wtypes/ne-wtypes-varenum)i [VariantClear](/windows/desktop/api/oleauto/nf-oleauto-variantclear) w Windows SDK.

##  <a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray

Pobiera tablicę bajtową z istniejącej tablicy wariantów

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*szybkość*<br/>
Odwołanie do istniejącego obiektu [CByteArray](../../mfc/reference/cbytearray-class.md) .

##  <a name="operator_lpcvariant"></a>COleVariant:: operator LPCVARIANT

Ten operator rzutowania zwraca `VARIANT` strukturę, której wartość jest kopiowana `COleVariant` z tego obiektu.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Uwagi

##  <a name="operator_lpvariant"></a>COleVariant:: operator LPVARIANT

Wywołaj ten operator rzutowania, aby `VARIANT` uzyskać dostęp do `COleVariant` źródłowej struktury tego obiektu.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Zmiana wartości w `VARIANT` strukturze, do której uzyskuje dostęp wskaźnik zwracany przez tę funkcję, spowoduje zmianę wartości tego `COleVariant` obiektu.

##  <a name="operator_eq"></a>COleVariant:: operator =

Te przeciążone operatory przypisania kopiują wartość źródłową `COleVariant` do tego obiektu.

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>Uwagi

Poniżej znajduje się krótki opis każdego z następujących operatorów:

- **operator = (** *varSrc* **)** Kopiuje istniejący element Variant lub `COleVariant` Object do tego obiektu.

- **operator = (** *pSrc* **)** Kopiuje obiekt VARIANT, do którego uzyskuje dostęp *pSrc* do tego obiektu.

- **operator = (** *lpszSrc* **)** Kopiuje ciąg zakończony znakiem null do tego obiektu i ustawia wartość VARTYPE na VT_BSTR.

- **operator = (** *strSrc* **)** Kopiuje obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) do tego obiektu i ustawia element VARTYPE na VT_BSTR.

- **operator = (** *nSrc* **)** Kopiuje wartość 8-lub 16-bitową liczbę całkowitą do tego obiektu. Jeśli *nSrc* jest wartością 8-bitową, typ VARTYPE jest ustawiony na VT_UI1. Jeśli *nSrc* jest wartością 16-bitową, a element VARTYPE jest VT_BOOL, jest przechowywany. w przeciwnym razie jest ustawiony na VT_I2.

- **operator = (** *lSrc* **)** Kopiuje 32-bitową wartość całkowitą do tego obiektu. Jeśli VARTYPE jest VT_ERROR, jest on przechowywany; w przeciwnym razie jest ustawiony na VT_I4.

- **operator = (** *curSrc* **)** Kopiuje obiekt [COleCurrency](../../mfc/reference/colecurrency-class.md) do tego obiektu i ustawia element VARTYPE na VT_CY.

- **operator = (** *fltSrc* **)** Kopiuje 32-bitową wartość zmiennoprzecinkową do tego obiektu i ustawia VARTYPE na VT_R4.

- **operator = (** *dblSrc* **)** Kopiuje 64-bitową wartość zmiennoprzecinkową do tego obiektu i ustawia VARTYPE na VT_R8.

- **operator = (** *dateSrc* **)** Kopiuje obiekt [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) do tego obiektu i ustawia element VARTYPE na VT_DATE.

- **operator = (** *arrSrc* **)** Kopiuje obiekt [CByteArray](../../mfc/reference/cbytearray-class.md) do tego `COleVariant` obiektu.

- **operator = (** *lbSrc* **)** Kopiuje obiekt [CLongBinary](../../mfc/reference/clongbinary-class.md) do tego `COleVariant` obiektu.

Aby uzyskać więcej informacji, zobacz zapisy [Variant](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) i [VarEnum](/windows/desktop/api/wtypes/ne-wtypes-varenum) w Windows SDK.

##  <a name="operator_eq_eq"></a>COleVariant:: operator = =

Ten operator porównuje dwie wartości wariantów i zwraca wartość różną od zera, jeśli są równe; w przeciwnym razie 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>COleVariant:: operator &lt;, &lt;&gt;&gt;

`CArchive` Wyprowadza wartość do lub`CdumpContext` i`COleVariant` wprowadza obiekt z `CArchive`. `COleVariant`

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>Uwagi

Operator `COleVariant` Wstaw ( **\<)obsługujezrzucaniediagnostycznei\<** przechowywanie w archiwum. Operator wyodrębniania **>>** () obsługuje ładowanie z archiwum.

##  <a name="setstring"></a>COleVariant:: SetString

Ustawia ciąg na konkretny typ.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parametry

*lpszSrc*<br/>
Ciąg zakończony znakiem null, który ma zostać skopiowany do `COleVariant` nowego obiektu.

*VtSrc*<br/>
Wartość VARTYPE dla nowego `COleVariant` obiektu.

### <a name="remarks"></a>Uwagi

Parametr *vtSrc* musi mieć wartość VT_BSTR (Unicode) lub VT_BSTRT (ANSI). `SetString`jest zazwyczaj używany do ustawiania ciągów do ANSI, ponieważ wartością domyślną dla konstruktora [COleVariant:: COleVariant](#colevariant) z parametrem ciągu lub ciągiem wskaźnika, a żadna VARTYPE nie jest Unicode.

Zestaw rekordów DAO w kompilacji inne niż UNICODE oczekuje ciągów jako ANSI. W tym celu w przypadku funkcji DAO `COleVariant` , które używają obiektów, jeśli nie tworzysz zestawu rekordów Unicode, należy użyć formy **COleVariant:: COleVariant (** *lpszSrc* **,** *vtSrc* **)** konstruktora z *vtSrc* Set na VT _BSTRT (ANSI) lub używane `SetString` z *vtSrc* ustawionym na VT_BSTRT, aby tworzyć ciągi ANSI. Na przykład `CDaoRecordset` funkcje [CDaoRecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek) i [CDaoRecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) używają `COleVariant` obiektów jako parametrów. Te obiekty muszą mieć wartość ANSI, jeśli zestaw rekordów DAO nie jest UNICODE.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
