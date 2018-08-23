---
title: Klasa COleVariant | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b7501adf2f424f2232df05e26f5d0ac4a35158c
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42465192"
---
# <a name="colevariant-class"></a>Klasa COleVariant
Hermetyzuje [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) typu danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleVariant::COleVariant](#colevariant)|Konstruuje `COleVariant` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleVariant::Attach](#attach)|Dołącza wariant do `COleVariant`.|  
|[COleVariant::ChangeType](#changetype)|Zmienia typ wariantu `COleVariant` obiektu.|  
|[COleVariant::Clear](#clear)|Czyści to `COleVariant` obiektu.|  
|[COleVariant::Detach](#detach)|Odłącza wariant ze `COleVariant` i zwraca typ VARIANT.|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Pobiera tablicę bajtów z istniejącej tablicy variant.|  
|[COleVariant::SetString](#setstring)|Ustawia ciąg do określonego typu, zazwyczaj ANSI.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Konwertuje `COleVariant` wartością do `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Konwertuje `COleVariant` do obiektu `LPVARIANT`.|  
|[COleVariant::operator =](#operator_eq)|Kopiuje `COleVariant` wartość.|  
|[COleVariant::operator ==](#operator_eq_eq)|Porównuje dwa `COleVariant` wartości.|  
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Dane wyjściowe `COleVariant` wartość `CArchive` lub `CDumpContext` i danych wejściowych `COleVariant` obiektu z `CArchive`.|  
  
## <a name="remarks"></a>Uwagi  
 Ten typ danych jest używany w automatyzacji OLE. W szczególności [DISPPARAMS](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagdispparams) struktura zawiera wskaźnik do tablicy struktur wariant. A `DISPPARAMS` struktury jest używany do przekazywania parametrów do [uwzględniając](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).  
  
> [!NOTE]
>  Ta klasa jest pochodną `VARIANT` struktury. Oznacza to, że można przekazać `COleVariant` w parametrze wywołuje `VARIANT` i składowych danych `VARIANT` struktury są elementami członkowskimi dane dostępne `COleVariant`.  
  
 Dwa powiązanych klas MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) i [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) hermetyzacji typy danych variant waluty ( `VT_CY`) Data i godzina ( `VT_DATE`). `COleVariant` Klasy są często używane klasy DAO; Zobacz te klasy w typowy sposób użycia tej klasy, na przykład [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [waluty](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagdispparams), i [uwzględniając](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) wpisów w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat `COleVariant` klasy i jego użycia w automatyzacji OLE, zobacz "Przekazywanie parametrów w automatyzacji OLE" w artykule [automatyzacji](../../mfc/automation.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="attach"></a>  COleVariant::Attach  
 Wywołaj tę funkcję, aby dołączyć danego [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) obiekt do bieżącego `COleVariant` obiektu.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 Istniejące `VARIANT` obiekt dołączony do bieżącego `COleVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta ustawia [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) z *varSrc* do VT_EMPTY.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) i [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) wpisów w zestawie Windows SDK.  
  
##  <a name="colevariant"></a>  COleVariant::COleVariant  
 Konstruuje `COleVariant` obiektu.  
  
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
 *varSrc*  
 Istniejące `COleVariant` lub `VARIANT` obiektu do skopiowania w nowe `COleVariant` obiektu.  
  
 *pSrc*  
 Wskaźnik do `VARIANT` obiektów, które mają zostać skopiowane do nowego `COleVariant` obiektu.  
  
 *lpszSrc*  
 Ciąg zakończony wartością null do skopiowania w nowe `COleVariant` obiektu.  
  
 *vtSrc*  
 `VARTYPE` Dla nowego `COleVariant` obiektu.  
  
 *strSrc*  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu do skopiowania w nowe `COleVariant` obiektu.  
  
 *nSrc*, *lSrc*  
 Wartość liczbową do skopiowania w nowe `COleVariant` obiektu.  
  
 *vtSrc*  
 `VARTYPE` Dla nowego `COleVariant` obiektu.  
  
 *curSrc*  
 A [COleCurrency](../../mfc/reference/colecurrency-class.md) obiektu do skopiowania w nowe `COleVariant` obiektu.  
  
 *fltSrc*, *dblSrc*  
 Wartość liczbową do skopiowania w nowe `COleVariant` obiektu.  
  
 *timeSrc*  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu do skopiowania w nowe `COleVariant` obiektu.  
  
 *arrSrc*  
 A [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu do skopiowania w nowe `COleVariant` obiektu.  
  
 *lbSrc*  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) obiektu do skopiowania w nowe `COleVariant` obiektu.  
  
 *PIDL*  
 Wskaźnik do [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) struktury do skopiowania w nowe `COleVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Te konstruktory tworzenia nowych `COleVariant` obiektów inicjowane z podaną wartością. Krótki opis każdego z tych konstruktorów poniżej.  
  
- **(COleVariant)** utworzy pustą `COleVariant` obiektu, VT_EMPTY.  
  
- **COleVariant (** *varSrc* **)** kopiuje istniejącą `VARIANT` lub `COleVariant` obiektu. Typ wariantu są zachowywane.  
  
- **COleVariant (** `pSrc` **)** kopiuje istniejącą `VARIANT` lub `COleVariant` obiektu. Typ wariantu są zachowywane.  
  
- **COleVariant (** `lpszSrc` **)** kopiuje ciąg do nowego obiektu VT_BSTR (UNICODE).  
  
- **COleVariant (** `lpszSrc` **,** `vtSrc` **)** kopiuje ciąg do nowego obiektu. Parametr *vtSrc* musi być VT_BSTR (UNICODE) lub VT_BSTRT (ANSI).  
  
- **COleVariant (** `strSrc` **)** kopiuje ciąg do nowego obiektu VT_BSTR (UNICODE).  
  
- **COleVariant (** `nSrc` **)** 8-bitową liczbę całkowitą są kopiowane do nowego obiektu, VT_UI1.  
  
- **COleVariant (** `nSrc` **,** `vtSrc` **)** kopiuje 16-bitową liczbę całkowitą (lub wartość logiczna) do nowego obiektu. Parametr *vtSrc* musi być VT_I2 lub VT_BOOL.  
  
- **COleVariant (** `lSrc` **,** `vtSrc` **)** kopiuje 32-bitowa liczba całkowita (lub wartość SCODE) do nowego obiektu. Parametr *vtSrc* musi być VT_I4, VT_ERROR lub VT_BOOL.  
  
- **COleVariant (** `curSrc` **)** kopie `COleCurrency` wartość do nowego obiektu VT_CY.  
  
- **COleVariant (** `fltSrc` **)** kopiuje 32-bitową wartość zmiennoprzecinkowa do nowego obiektu, VT_R4.  
  
- **COleVariant (** `dblSrc` **)** kopiuje wartość zmiennoprzecinkową 64-bitowego do nowego obiektu, VT_R8.  
  
- **COleVariant (** `timeSrc` **)** kopie `COleDateTime` wartość do nowego obiektu VT_DATE.  
  
- **COleVariant (** `arrSrc` **)** kopie `CByteArray` obiektu do nowego obiektu, VT_EMPTY.  
  
- **COleVariant (** `lbSrc` **)** kopie `CLongBinary` obiektu do nowego obiektu, VT_EMPTY.  
  
 Aby uzyskać więcej informacji na temat SCODE, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
##  <a name="changetype"></a>  COleVariant::ChangeType  
 Konwertuje typ wariantu wartości w tym `COleVariant` obiektu.  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *VarType*  
 [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) tego `COleVariant` obiektu.  
  
 *pSrc*  
 Wskaźnik do [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) obiekt do skonwertowania. Jeśli ta wartość wynosi NULL, to `COleVariant` obiekt jest używany jako źródło dla konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), i [VariantChangeType](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantchangetype) wpisów w zestawie Windows SDK.  
  
##  <a name="clear"></a>  COleVariant::Clear  
 Czyści `VARIANT`.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 VT_EMPTY to ustawia VARTYPE dla tego obiektu. `COleVariant` Destruktor wywołuje tę funkcję.  
  
 Aby uzyskać więcej informacji, zobacz `VARIANT`, typ ZMIENNEJ, a `VariantClear` wpisów w zestawie Windows SDK.  
  
##  <a name="detach"></a>  COleVariant::Detach  
 Odłącza bazowego [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) obiektu z tego `COleVariant` obiektu.  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta ustawia [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) tego `COleVariant` obiektu VT_EMPTY.  
  
> [!NOTE]
>  Po wywołaniu `Detach`, odpowiada za wywołującego wywołać `VariantClear` na wynikającej `VARIANT` struktury.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), i [VariantClear](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantclear) wpisów w zestawie Windows SDK.  
  
##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray  
 Pobiera tablicę bajtów z istniejącej tablicy typu variant  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parametry  
 *Bajty*  
 Odwołanie do istniejącego [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu.  
  
##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT  
 Ten operator rzutowania zwraca `VARIANT` struktury, którego wartość jest kopiowany z tym `COleVariant` obiektu.  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT  
 Wywołanie tego operatora rzutowania do dostępu do podstawowych `VARIANT` struktury, w tym `COleVariant` obiektu.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Zmiana wartości w `VARIANT` struktury używane przez wskaźnik zwracany przez tę funkcję zmieni wartość tego `COleVariant` obiektu.  
  
##  <a name="operator_eq"></a>  COleVariant::operator =  
 Te operatory przeciążone przypisania skopiowany wartość źródłowa to `COleVariant` obiektu.  
  
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
 Krótki opis każdego operatora następująco:  
  
- **Operator = (** *varSrc ***)** kopiuje istniejący typ VARIANT lub `COleVariant` obiektu do tego obiektu.  
  
- **Operator = (** `pSrc` **)** kopiuje obiekt wariant uzyskują *pSrc* do tego obiektu.  
  
- **Operator = (** `lpszSrc` **)** kopiuje ciąg zakończony wartością null do tego obiektu i ustawia VARTYPE VT_BSTR.  
  
- **Operator = (** `strSrc` **)** kopie [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu do tego obiektu i zestawy VARTYPE do VT_BSTR.  
  
- **Operator = (** `nSrc` **)** kopiuje wartość całkowitą 8 lub 16-bitowych do tego obiektu. Jeśli *nSrc* 8-bitową wartość VARTYPE tego jest równa VT_UI1. Jeśli *nSrc* jest wartością 16-bitową i VARTYPE tego jest VT_BOOL., jest zachowany; w przeciwnym razie, jest równa VT_I2.  
  
- **Operator = (** `lSrc` **)** skopiowanie wartości 32-bitową liczbę całkowitą do tego obiektu. Jeśli VARTYPE tego VT_ERROR, jest przechowywana; w przeciwnym razie ustawiana jest na VT_I4.  
  
- **Operator = (** `curSrc` **)** kopie [COleCurrency](../../mfc/reference/colecurrency-class.md) obiektu do tego obiektu i zestawy VARTYPE do VT_CY.  
  
- **Operator = (** `fltSrc` **)** kopiuje 32-bitową wartość zmiennoprzecinkowa do tego obiektu i ustawia VARTYPE VT_R4.  
  
- **Operator = (** `dblSrc` **)** kopiuje wartość zmiennoprzecinkową 64-bitowego do tego obiektu i ustawia VARTYPE VT_R8.  
  
- **Operator = (** `dateSrc` **)** kopie [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu do tego obiektu i zestawy VARTYPE do VT_DATE.  
  
- **Operator = (** `arrSrc` **)** kopie [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu do tego `COleVariant` obiektu.  
  
- **Operator = (** `lbSrc` **)** kopie [CLongBinary](../../mfc/reference/clongbinary-class.md) obiektu do tego `COleVariant` obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) i [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) wpisów w zestawie Windows SDK.  
  
##  <a name="operator_eq_eq"></a>  COleVariant::operator ==  
 Ten operator porównuje dwie wartości typu variant i zwraca wartość różną od zera, jeśli są równe; w przeciwnym razie 0.  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;  
 Dane wyjściowe `COleVariant` wartość `CArchive` lub `CdumpContext` i danych wejściowych `COleVariant` obiektu z `CArchive`.  
  
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
 `COleVariant` Wstawiania ( **< \<**) operator obsługuje diagnostycznych zrzucanie i przechowywania do archiwum. Wyodrębnianie ( **>>**) — operator obsługuje ładowanie z archiwum.  
  
##  <a name="setstring"></a>  COleVariant::SetString  
 Ustawia ciąg do określonego typu.  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSrc*  
 Ciąg zakończony wartością null do skopiowania w nowe `COleVariant` obiektu.  
  
 *vtSrc*  
 VARTYPE nowego `COleVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *vtSrc* musi być VT_BSTR (UNICODE) lub VT_BSTRT (ANSI). `SetString` Zazwyczaj służy do zestawu ciągów do ANSI, ponieważ wartość domyślna dla [COleVariant::COleVariant](#colevariant) Konstruktor ciągu lub parametru wskaźnika ciągu, nie VARTYPE jest UNICODE.  
  
 Zestaw rekordów DAO w kompilacji innego niż UNICODE oczekuje, że ciągi jako ANSI. W związku z tym, do DAO funkcji używających `COleVariant` obiektów są nietworzenie zestawu rekordów UNICODE, należy użyć **COleVariant::COleVariant (** `lpszSrc` **,** `vtSrc` **)**  formularza konstruktora z *vtSrc* ustawić VT_BSTRT (ANSI) lub użyć `SetString` z *vtSrc* równa VT_BSTRT się ciągów ANSI. Na przykład `CDaoRecordset` funkcje [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) i [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) użyj `COleVariant` obiektów jako parametrów. Te obiekty muszą być ANSI, jeśli zestaw rekordów DAO nie jest UNICODE.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



