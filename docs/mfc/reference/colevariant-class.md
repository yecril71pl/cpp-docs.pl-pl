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
ms.openlocfilehash: f907ed7c058f87cf03530411bc8fa4a3c108a4f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374821"
---
# <a name="colevariant-class"></a>Klasa COleVariant

Hermetyzuje typ danych [VARIANT.](/windows/win32/api/oaidl/ns-oaidl-variant)

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
|[COleVariant::Dołącz](#attach)|Dołącza wariant do `COleVariant`pliku .|
|[COleVariant::ChangeType](#changetype)|Zmienia typ wariantu `COleVariant` tego obiektu.|
|[COleVariant::Wyczyść](#clear)|Czyści `COleVariant` ten obiekt.|
|[COleVariant::Detach](#detach)|Odłącza wariant od `COleVariant` a i zwraca wariant.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Pobiera tablicę bajtów z istniejącej tablicy wariantów.|
|[COleVariant::SetString](#setstring)|Ustawia ciąg na określony typ, zazwyczaj ANSI.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Konwertuje `COleVariant` wartość `LPCVARIANT`na plik .|
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Konwertuje `COleVariant` obiekt `LPVARIANT`na plik .|
|[COleVariant::operator =](#operator_eq)|Kopiuje `COleVariant` wartość.|
|[COleVariant::operator ==](#operator_eq_eq)|Porównuje dwie `COleVariant` wartości.|
|[COleVariant::operator &lt; &lt;,&gt;&gt;](#operator_lt_lt__gt_gt)|`COleVariant` Wyprowadza wartość do `CArchive` `CDumpContext` lub i `COleVariant` wprowadza `CArchive`obiekt z .|

## <a name="remarks"></a>Uwagi

Ten typ danych jest używany w automatyzacji OLE. W szczególności [STRUKTURA DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) zawiera wskaźnik do tablicy struktur VARIANT. Struktura `DISPPARAMS` służy do przekazywania parametrów do [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

> [!NOTE]
> Ta klasa jest pochodną `VARIANT` struktury. Oznacza to, że `COleVariant` można przekazać w `VARIANT` parametr, który wymaga `VARIANT` a i że `COleVariant`elementy członkowskie danych struktury są dostępne elementy członkowskie danych .

Dwie powiązane klasy MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) i [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) hermetyzują `VT_CY`typy `VT_DATE`danych wariantu CURRENCY ( ) i DATE ( ). Klasa `COleVariant` jest szeroko stosowana w klasach DAO; zobacz te klasy dla typowego użycia tej klasy, na przykład [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Aby uzyskać więcej informacji, zobacz [WARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [WALUTA](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)i [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) wpisów w windows SDK.

Aby uzyskać więcej `COleVariant` informacji na temat klasy i jej zastosowania w automatyzacji OLE, zobacz "Przekazywanie parametrów w automatyzacji OLE" w artykule [Automatyzacja](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant::Dołącz

Wywołanie tej funkcji, aby dołączyć `COleVariant` dany obiekt [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) do bieżącego obiektu.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parametry

*varSrc ( varSrc )*<br/>
Istniejący `VARIANT` obiekt, który ma `COleVariant` zostać dołączony do bieżącego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia VARTYPE *varSrc* na VT_EMPTY.

Aby uzyskać więcej informacji, zobacz pozycje [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) i [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) w sdk systemu Windows.

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant::COleVariant

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

*varSrc ( varSrc )*<br/>
Istniejący `COleVariant` `VARIANT` lub obiekt do skopiowania `COleVariant` do nowego obiektu.

*Psrc*<br/>
Wskaźnik do `VARIANT` obiektu, który zostanie skopiowany `COleVariant` do nowego obiektu.

*lpszsrc*<br/>
Ciąg zakończony z wartością null ma `COleVariant` zostać skopiowany do nowego obiektu.

*Vtsrc*<br/>
Dla `VARTYPE` nowego `COleVariant` obiektu.

*strSrc ( strSrc )*<br/>
Obiekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) do skopiowania do `COleVariant` nowego obiektu.

*nSrc*, *lSrc* Wartość liczbowa do skopiowania do nowego `COleVariant` obiektu.

*Vtsrc*<br/>
Dla `VARTYPE` nowego `COleVariant` obiektu.

*curSrc ( curSrc )*<br/>
A [COleCurrency](../../mfc/reference/colecurrency-class.md) obiekt do skopiowania `COleVariant` do nowego obiektu.

*fltSrc*, *dblSrc*<br/>
Wartość liczbowa, która ma zostać `COleVariant` skopiowana do nowego obiektu.

*czasSrc*<br/>
A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt do skopiowania `COleVariant` do nowego obiektu.

*arrSrc ( arrSrc )*<br/>
A [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu do skopiowania `COleVariant` do nowego obiektu.

*lbSrc ( lbSrc )*<br/>
A [CLongBinary](../../mfc/reference/clongbinary-class.md) obiektu do skopiowania `COleVariant` do nowego obiektu.

*pidl*<br/>
Wskaźnik do [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) struktury do skopiowania `COleVariant` do nowego obiektu.

### <a name="remarks"></a>Uwagi

Wszystkie te konstruktory utworzyć nowe `COleVariant` obiekty zainicjowane do określonej wartości. Krótki opis każdego z tych konstruktorów następuje.

- **COleVariant( )** Tworzy pusty `COleVariant` obiekt, VT_EMPTY.

- **COleVariant(** *varSrc* **)** Kopiuje `VARIANT` istniejący lub `COleVariant` obiekt. Typ wariantu jest zachowywany.

- **COleVariant(** *pSrc* **)** Kopiuje `VARIANT` istniejący lub `COleVariant` obiekt. Typ wariantu jest zachowywany.

- **COleVariant(** *lpszSrc* **)** Kopiuje ciąg do nowego obiektu, VT_BSTR (UNICODE).

- **COleVariant(** *lpszSrc* **,** *vtSrc* **)** Kopiuje ciąg do nowego obiektu. Parametr *vtSrc* musi być VT_BSTR (UNICODE) lub VT_BSTRT (ANSI).

- **COleVariant(** *strSrc* **)** Kopiuje ciąg do nowego obiektu, VT_BSTR (UNICODE).

- **COleVariant(** *nSrc* **)** Kopiuje 8-bitową całkowitej liczby do nowego obiektu, VT_UI1.

- **COleVariant(** *nSrc* **,** *vtSrc* **)** Kopiuje 16-bitową całkowitej liczby (lub wartości logicznej) do nowego obiektu. Parametr *vtSrc* musi być VT_I2 lub VT_BOOL.

- **COleVariant(** *lSrc* **,** *vtSrc* **)** Kopiuje 32-bitową całkowitej liczby (lub SCODE wartość) do nowego obiektu. Parametr *vtSrc* musi być VT_I4, VT_ERROR lub VT_BOOL.

- **COleVariant(** *curSrc* **)** Kopiuje `COleCurrency` wartość do nowego obiektu, VT_CY.

- **COleVariant(** *fltSrc* **)** Kopiuje 32-bitową wartość zmiennoprzecinkową do nowego obiektu, VT_R4.

- **COleVariant(** *dblSrc* **)** Kopiuje 64-bitową wartość zmiennoprzecinkową do nowego obiektu, VT_R8.

- **COleVariant(** *timeSrc* **)** Kopiuje `COleDateTime` wartość do nowego obiektu, VT_DATE.

- **COleVariant(** *arrSrc* **)** Kopiuje `CByteArray` obiekt do nowego obiektu, VT_EMPTY.

- **COleVariant(** *lbSrc* **)** Kopiuje `CLongBinary` obiekt do nowego obiektu, VT_EMPTY.

Aby uzyskać więcej informacji na temat SCODE, zobacz [Struktura kodów błędów COM](/windows/win32/com/structure-of-com-error-codes) w windows SDK.

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant::ChangeType

Konwertuje typ wartości wariantu w tym `COleVariant` obiekcie.

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*Vartype*<br/>
Typ VARTYPE `COleVariant` dla tego obiektu.

*Psrc*<br/>
Wskaźnik do [variant](/windows/win32/api/oaidl/ns-oaidl-variant) obiektu do konwersji. Jeśli ta wartość jest `COleVariant` NULL, ten obiekt jest używany jako źródło konwersji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [pozycje VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)i [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) w sdk systemu Windows.

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant::Wyczyść

Czyści `VARIANT`plik .

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Spowoduje to ustawienie vartype dla tego obiektu do VT_EMPTY. Destruktor `COleVariant` wywołuje tę funkcję.

Aby uzyskać więcej `VARIANT`informacji, zobacz `VariantClear` , VARTYPE i wpisy w windows SDK.

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::Detach

Odłącza podstawowy [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) obiekt VARIANT `COleVariant` od tego obiektu.

```
VARIANT Detach();
```

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia vartype `COleVariant` dla tego obiektu do VT_EMPTY.

> [!NOTE]
> Po `Detach`wywołaniu , jest odpowiedzialny za `VariantClear` wywołanie wynikowej `VARIANT` struktury.

Aby uzyskać więcej informacji, zobacz pozycje [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)i [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) w sdk systemu Windows.

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray

Pobiera tablicę bajtów z istniejącej tablicy wariantu

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parametry

*Bajtów*<br/>
Odwołanie do istniejącego [obiektu CByteArray.](../../mfc/reference/cbytearray-class.md)

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant::operator LPCVARIANT

Ten operator rzutowania zwraca strukturę, `VARIANT` `COleVariant` której wartość jest kopiowana z tego obiektu.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Uwagi

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant::operator LPVARIANT

Wywołanie tego operatora rzutowania, aby uzyskać dostęp do podstawowej `VARIANT` struktury dla tego `COleVariant` obiektu.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Uwagi

> [!CAUTION]
> Zmiana wartości w `VARIANT` strukturze dostępnej za pomocą wskaźnika zwróconego `COleVariant` przez tę funkcję spowoduje zmianę wartości tego obiektu.

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant::operator =

Te przeciążonych operatorów przypisania `COleVariant` skopiować wartość źródłową do tego obiektu.

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

Krótki opis każdego operatora jest następujący:

- **operator =(** *varSrc* **)** Kopiuje istniejący `COleVariant` wariant lub obiekt do tego obiektu.

- **operator =(** *pSrc* **)** Kopiuje obiekt VARIANT, do który pSrc uzyskuje dostęp przez *pSrc.*

- **operator =(** *lpszSrc* **)** Kopiuje ciąg zakończony zerem do tego obiektu i ustawia vartype na VT_BSTR.

- **operator =(** *strSrc* **)** Kopiuje [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu do tego obiektu i ustawia VARTYPE do VT_BSTR.

- **operator =(** *nSrc* **)** Kopiuje 8- lub 16-bitową wartość całkowitą do tego obiektu. Jeśli *nSrc* jest wartością 8-bitową, wartość VARTYPE tego jest ustawiona na VT_UI1. Jeśli *nSrc* jest wartością 16-bitową, a wartość VARTYPE tego jest VT_BOOL, jest zachowywana; w przeciwnym razie jest ustawiona na VT_I2.

- **operator =(** *lSrc* **)** Kopiuje 32-bitową wartość całkowitą do tego obiektu. Jeśli VT_ERROR jest VT_ERROR, jest on zachowywany; w przeciwnym razie jest ustawiona na VT_I4.

- **operator =(** *curSrc* **)** Kopiuje [COleCurrency](../../mfc/reference/colecurrency-class.md) obiektu do tego obiektu i ustawia VARTYPE do VT_CY.

- **operator =(** *fltSrc* **)** Kopiuje 32-bitową wartość zmiennoprzecinkową do tego obiektu i ustawia wartość VARTYPE na VT_R4.

- **operator =(** *dblSrc* **)** Kopiuje 64-bitową wartość zmiennoprzecinkową do tego obiektu i ustawia wartość VARTYPE na VT_R8.

- **operator =(** *dateSrc* **)** Kopiuje [obiekt COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) do tego obiektu i ustawia vartype na VT_DATE.

- **operator =(** *arrSrc* **)** Kopiuje obiekt [CByteArray](../../mfc/reference/cbytearray-class.md) do tego `COleVariant` obiektu.

- **operator =(** *lbSrc* **)** Kopiuje [obiekt CLongBinary](../../mfc/reference/clongbinary-class.md) do tego `COleVariant` obiektu.

Aby uzyskać więcej informacji, zobacz pozycje [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) i [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) w sdk systemu Windows.

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant::operator ==

Ten operator porównuje dwie wartości wariantu i zwraca wartość niezerową, jeśli są równe; w przeciwnym razie 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant::operator &lt; &lt;,&gt;&gt;

`COleVariant` Wyprowadza wartość do `CArchive` `CdumpContext` lub i `COleVariant` wprowadza `CArchive`obiekt z .

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

Operator `COleVariant` wstawiania (**\<**) obsługuje diagnostykę dumpingu i przechowywania w archiwum. Operator ekstrakcji (**>>**) obsługuje ładowanie z archiwum.

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant::SetString

Ustawia ciąg na określony typ.

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parametry

*lpszsrc*<br/>
Ciąg zakończony z wartością null ma `COleVariant` zostać skopiowany do nowego obiektu.

*Vtsrc*<br/>
Vartype dla nowego `COleVariant` obiektu.

### <a name="remarks"></a>Uwagi

Parametr *vtSrc* musi być VT_BSTR (UNICODE) lub VT_BSTRT (ANSI). `SetString`jest zwykle używany do ustawiania ciągów do ANSI, ponieważ domyślny dla [konstruktora COleVariant::COleVariant](#colevariant) z parametrem wskaźnika ciągu lub ciągu i nie VARTYPE jest UNICODE.

Plik rekordów DAO w kompilacji innych niż UNICODE oczekuje, że ciągi będą ANSI. Tak więc dla funkcji `COleVariant` DAO, które używają obiektów, jeśli nie tworzysz zestawu rekordów UNICODE, należy użyć **COleVariant::COleVariant(** *lpszSrc* **,** *vtSrc* **)** forma konstruktora z *vtSrc* ustawiona na VT_BSTRT (ANSI) lub użyć `SetString` z *vtSrc* ustawiony na VT_BSTRT do tworzenia ciągów ANSI. Na przykład `CDaoRecordset` funkcje [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) i [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) używa `COleVariant` obiektów jako parametrów. Obiekty te muszą być ANSI, jeśli plik rekordów DAO nie jest UNICODE.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
