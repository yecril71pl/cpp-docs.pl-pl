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
ms.openlocfilehash: 0966aa28595d5384fd6877f30452d3cc24853f29
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079212"
---
# <a name="colevariant-class"></a>Klasa COleVariant
Hermetyzuje [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) — typ danych.  
  
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
|[COleVariant::Attach](#attach)|Dołącza **VARIANT** do `COleVariant`.|  
|[COleVariant::ChangeType](#changetype)|Zmienia typ wariantu `COleVariant` obiektu.|  
|[COleVariant::Clear](#clear)|Czyści to `COleVariant` obiektu.|  
|[COleVariant::Detach](#detach)|Odłącza **VARIANT** z `COleVariant` i zwraca **VARIANT**.|  
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Pobiera tablicę bajtów z tablicy istniejące wariantu.|  
|[COleVariant::SetString](#setstring)|Ustawia ciąg do określonego typu, zazwyczaj ANSI.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Konwertuje `COleVariant` wartości do `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Konwertuje `COleVariant` obiekt do `LPVARIANT`.|  
|[COleVariant::operator =](#operator_eq)|Kopie `COleVariant` wartość.|  
|[COleVariant::operator ==](#operator_eq_eq)|Porównuje dwa `COleVariant` wartości.|  
|[COleVariant::operator &lt; &lt;, &gt;&gt;](#operator_lt_lt__gt_gt)|Dane wyjściowe `COleVariant` do wartości `CArchive` lub `CDumpContext` i danych wejściowych `COleVariant` obiekt z `CArchive`.|  
  
## <a name="remarks"></a>Uwagi  
 Ten typ danych jest używany w automatyzacji OLE. W szczególności [DISPPARAMS](http://msdn.microsoft.com/a16e5a21-766e-4287-b039-13429aa78f8b) struktura zawiera wskaźnik do tablicy **VARIANT** struktury. A **DISPPARAMS** struktura jest używana do przekazania parametrów do [IDispatch::Invoke](http://msdn.microsoft.com/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
> [!NOTE]
>  Ta klasa pochodzi od **VARIANT** struktury. Oznacza to, że można przekazać `COleVariant` w parametr, który odwołuje się do **VARIANT** i elementów członkowskich danych **VARIANT** struktury są elementami członkowskimi danych dostępny `COleVariant`.  
  
 Dwa powiązanych klas MFC [COleCurrency](../../mfc/reference/colecurrency-class.md) i [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) Hermetyzowanie typów danych variant **waluty** ( `VT_CY`) i **data** ( `VT_DATE`). `COleVariant` Bardzo często używane klasy w klasach DAO; Zobacz te klasy w typowy sposób użycia tej klasy, na przykład [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [waluty](http://msdn.microsoft.com/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](http://msdn.microsoft.com/a16e5a21-766e-4287-b039-13429aa78f8b), i [IDispatch::Invoke](http://msdn.microsoft.com/964ade8e-9d8a-4d32-bd47-aa678912a54d) wpisów w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji na temat `COleVariant` klasy i jego użycia w automatyzacji OLE, zobacz "Przekazywanie parametrów w automatyzacji OLE" w artykule [automatyzacji](../../mfc/automation.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagVARIANT`  
  
 `COleVariant`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="attach"></a>  COleVariant::Attach  
 Wywołanie tej funkcji można dołączyć podanego [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) obiektu do bieżącego `COleVariant` obiektu.  
  
```  
void Attach(VARIANT& varSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *varSrc*  
 Istniejące **VARIANT** obiektu jest dołączony do bieżącego `COleVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja ustawia [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) z *varSrc* do `VT_EMPTY`.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) i [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) wpisów w zestawie Windows SDK.  
  
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
 Istniejące `COleVariant` lub **VARIANT** obiekt ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
 *pSrc*  
 Wskaźnik do **VARIANT** obiektów, które zostaną skopiowane do nowego `COleVariant` obiektu.  
  
 *lpszSrc*  
 Ciąg zakończony zerem, można skopiować do nowego `COleVariant` obiektu.  
  
 *vtSrc*  
 `VARTYPE` Nowego `COleVariant` obiektu.  
  
 *strSrc*  
 A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
 *nSrc*, *lSrc*  
 Wartość liczbową można skopiować do nowego `COleVariant` obiektu.  
  
 *vtSrc*  
 `VARTYPE` Nowego `COleVariant` obiektu.  
  
 *curSrc*  
 A [COleCurrency](../../mfc/reference/colecurrency-class.md) obiekt ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
 *fltSrc*, *dblSrc*  
 Wartość liczbową można skopiować do nowego `COleVariant` obiektu.  
  
 *timeSrc*  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
 *arrSrc*  
 A [CByteArray](../../mfc/reference/cbytearray-class.md) obiekt ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
 *lbSrc*  
 A [clongbinary —](../../mfc/reference/clongbinary-class.md) obiekt ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
 *PIDL*  
 Wskaźnik do [ITEMIDLIST](http://msdn.microsoft.com/library/windows/desktop/bb773321) struktury ma zostać skopiowany do nowego `COleVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie te konstruktorów tworzenia nowych `COleVariant` obiektów zainicjowany z podaną wartością. Następuje krótki opis każdego z tych konstruktorów.  
  
- **(COleVariant)** tworzy pustą `COleVariant` obiektu `VT_EMPTY`.  
  
- **COleVariant (** *varSrc* **)** umożliwia skopiowanie istniejącej **VARIANT** lub `COleVariant` obiektu. Typ wariantu są zachowywane.  
  
- **COleVariant (** `pSrc` **)** umożliwia skopiowanie istniejącej **VARIANT** lub `COleVariant` obiektu. Typ wariantu są zachowywane.  
  
- **COleVariant (** `lpszSrc` **)** kopiuje ciąg do nowego obiektu `VT_BSTR` (UNICODE).  
  
- **COleVariant (** `lpszSrc` **,** `vtSrc` **)** kopiuje ciąg do nowego obiektu. Parametr *vtSrc* musi być `VT_BSTR` (UNICODE) lub `VT_BSTRT` (ANSI).  
  
- **COleVariant (** `strSrc` **)** kopiuje ciąg do nowego obiektu **VT_BSTR** (UNICODE).  
  
- **COleVariant (** `nSrc` **)** 8-bitową liczbę całkowitą są kopiowane do nowego obiektu `VT_UI1`.  
  
- **COleVariant (** `nSrc` **,** `vtSrc` **)** 16-bitową liczbę całkowitą (lub wartość logiczna) są kopiowane do nowego obiektu. Parametr *vtSrc* musi być `VT_I2` lub `VT_BOOL`.  
  
- **COleVariant (** `lSrc` **,** `vtSrc` **)** kopiuje 32-bitową liczbę całkowitą (lub `SCODE` wartość) do nowego obiektu. Parametr *vtSrc* musi być `VT_I4`, `VT_ERROR`, lub `VT_BOOL`.  
  
- **COleVariant (** `curSrc` **)** kopie **COleCurrency** wartości do nowego obiektu `VT_CY`.  
  
- **COleVariant (** `fltSrc` **)** 32-bitową wartość zmiennoprzecinkowe są kopiowane do nowego obiektu `VT_R4`.  
  
- **COleVariant (** `dblSrc` **)** 64-bitowej wartości zmiennoprzecinkowej są kopiowane do nowego obiektu `VT_R8`.  
  
- **COleVariant (** `timeSrc` **)** kopie `COleDateTime` wartości do nowego obiektu `VT_DATE`.  
  
- **COleVariant (** `arrSrc` **)** kopie `CByteArray` obiektu do nowego obiektu `VT_EMPTY`.  
  
- **COleVariant (** `lbSrc` **)** kopie `CLongBinary` obiektu do nowego obiektu `VT_EMPTY`.  
  
 Aby uzyskać więcej informacji na temat `SCODE`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
##  <a name="changetype"></a>  COleVariant::ChangeType  
 Konwertuje typ wariantu wartości w tym `COleVariant` obiektu.  
  
```  
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *VarType*  
 [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) dla tego `COleVariant` obiektu.  
  
 *pSrc*  
 Wskaźnik do [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) obiektu do skonwertowania. Jeśli ta wartość jest **NULL**, to `COleVariant` obiekt jest używany jako źródło do konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), i [VariantChangeType](http://msdn.microsoft.com/48a51e32-95d7-4eeb-8106-f5043ffa2fd1) wpisów w zestawie Windows SDK.  
  
##  <a name="clear"></a>  COleVariant::Clear  
 Czyści **VARIANT**.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 To ustawienie **VARTYPE** dla tego obiektu do `VT_EMPTY`. `COleVariant` Destruktor wywoła tej funkcji.  
  
 Aby uzyskać więcej informacji, zobacz `VARIANT`, `VARTYPE`, i `VariantClear` wpisów w zestawie Windows SDK.  
  
##  <a name="detach"></a>  COleVariant::Detach  
 Odłącza odpowiadającego [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) obiektu z tego `COleVariant` obiektu.  
  
```  
VARIANT Detach();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja ustawia [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) tego `COleVariant` do obiektu `VT_EMPTY`.  
  
> [!NOTE]
>  Po wywołaniu `Detach`, odpowiada wywołującego wywołać **VariantClear** na powstałe w ten sposób **VARIANT** struktury.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118), [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4), i [VariantClear](http://msdn.microsoft.com/28741d81-8404-4f85-95d3-5c209ec13835) wpisów w zestawie Windows SDK.  
  
##  <a name="getbytearrayfromvariantarray"></a>  COleVariant::GetByteArrayFromVariantArray  
 Pobiera tablicę bajtów z tablicy istniejące wariantu  
  
```  
void GetByteArrayFromVariantArray(CByteArray& bytes);
```  
  
### <a name="parameters"></a>Parametry  
 *Bajty*  
 Odwołanie do istniejącej [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu.  
  
##  <a name="operator_lpcvariant"></a>  COleVariant::operator LPCVARIANT  
 Ten operator rzutowania zwraca `VARIANT` struktury, którego wartość jest kopiowana z to `COleVariant` obiektu.  
  
```  
operator LPCVARIANT() const; 
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="operator_lpvariant"></a>  COleVariant::operator LPVARIANT  
 Wywołanie tego operatora rzutowania do dostępu do podstawowych `VARIANT` to struktura `COleVariant` obiektu.  
  
```  
operator LPVARIANT();
```   
  
### <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Zmiana wartości w **VARIANT** struktury używane przez wskaźnik zwracane przez tę funkcję zmieni wartość tego `COleVariant` obiektu.  
  
##  <a name="operator_eq"></a>  COleVariant::operator =  
 Te operatory przypisania przeciążone skopiuj wartość źródła do tego `COleVariant` obiektu.  
  
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
  
- **Operator = (** *varSrc ***)** umożliwia skopiowanie istniejącej **VARIANT** lub `COleVariant` obiektu do tego obiektu.  
  
- **Operator = (** `pSrc` **)** kopie **VARIANT** obiektu uzyskiwał *pSrc* do tego obiektu.  
  
- **Operator = (** `lpszSrc` **)** kopiuje ciąg znaków zakończony znakiem null do tego obiektu i ustawia **VARTYPE** do `VT_BSTR`.  
  
- **Operator = (** `strSrc` **)** kopie [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiektu do tego obiektu i zestawy **VARTYPE** do `VT_BSTR`.  
  
- **Operator = (** `nSrc` **)** 8 lub 16-bitową liczbę całkowitą są kopiowane do tego obiektu. Jeśli *nSrc* jest 8-bitową wartość **VARTYPE** to jest ustawiony na wartość `VT_UI1`. Jeśli *nSrc* jest 16-bitową wartość i **VARTYPE** tego jest `VT_BOOL`, jest ona przechowywane; w przeciwnym razie, ma ustawioną wartość `VT_I2`.  
  
- **Operator = (** `lSrc` **)** wartość 32-bitową liczbę całkowitą są kopiowane do tego obiektu. Jeśli **VARTYPE** tego jest `VT_ERROR`, jest ona przechowywane; w przeciwnym razie, ma ustawioną wartość `VT_I4`.  
  
- **Operator = (** `curSrc` **)** kopie [COleCurrency](../../mfc/reference/colecurrency-class.md) obiektu do tego obiektu i zestawy **VARTYPE** do `VT_CY`.  
  
- **Operator = (** `fltSrc` **)** 32-bitową wartość zmiennoprzecinkowe są kopiowane do tego obiektu i ustawia **VARTYPE** do `VT_R4`.  
  
- **Operator = (** `dblSrc` **)** kopiuje wartość zmiennoprzecinkowa 64-bitowej do tego obiektu i ustawia **VARTYPE** do `VT_R8`.  
  
- **Operator = (** `dateSrc` **)** kopie [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu do tego obiektu i zestawy **VARTYPE** do `VT_DATE`.  
  
- **Operator = (** `arrSrc` **)** kopie [CByteArray](../../mfc/reference/cbytearray-class.md) obiektu do tego `COleVariant` obiektu.  
  
- **Operator = (** `lbSrc` **)** kopie [clongbinary —](../../mfc/reference/clongbinary-class.md) obiektu do tego `COleVariant` obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [VARIANT](http://msdn.microsoft.com/e305240e-9e11-4006-98cc-26f4932d2118) i [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) wpisów w zestawie Windows SDK.  
  
##  <a name="operator_eq_eq"></a>  COleVariant::operator ==  
 Ten operator porównuje dwie wartości typu variant i zwraca wartość niezerową, czy są równe; w przeciwnym razie 0.  
  
```  
BOOL operator==(const VARIANT& varSrc) const; 
BOOL operator==(LPCVARIANT pSrc) const;
```  
  
##  <a name="operator_lt_lt__gt_gt"></a>  COleVariant::operator &lt; &lt;, &gt;&gt;  
 Dane wyjściowe `COleVariant` do wartości `CArchive` lub **CdumpContext** i danych wejściowych `COleVariant` obiekt z `CArchive`.  
  
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
 `COleVariant` Wstawiania ( **< \<**) obsługuje operator diagnostycznych zrzucanie i przechowywania do archiwum. Wyodrębnianie ( **>>**) — operator obsługuje ładowanie z archiwum.  
  
##  <a name="setstring"></a>  COleVariant::SetString  
 Ustawia ciąg do określonego typu.  
  
```  
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSrc*  
 Ciąg zakończony zerem, można skopiować do nowego `COleVariant` obiektu.  
  
 *vtSrc*  
 **VARTYPE** nowego `COleVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Parametr *vtSrc* musi być `VT_BSTR` (UNICODE) lub `VT_BSTRT` (ANSI). `SetString` zwykle jest używana do ustawioną ciągów ANSI, ponieważ wartość domyślna dla [COleVariant::COleVariant](#colevariant) konstruktora z ciągu lub parametru wskaźnik ciągu i nie **VARTYPE** jest UNICODE.  
  
 Zestaw rekordów DAO kompilacji z systemem innym niż UNICODE oczekuje ciągów ANSI za. W związku z tym dla DAO funkcje używające `COleVariant` obiekty, jeśli nie utworzysz zestaw rekordów UNICODE, należy użyć **COleVariant::COleVariant (** `lpszSrc` **,** `vtSrc` **)**  forma konstruktora z *vtSrc* ustawioną `VT_BSTRT` (ANSI) lub użyj `SetString` z *vtSrc* ustawioną `VT_BSTRT` dokonanie ciągów ANSI. Na przykład `CDaoRecordset` funkcje [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) i [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) użyć `COleVariant` obiektów jako parametry. Te obiekty muszą być ANSI, jeśli zestaw rekordów DAO nie jest UNICODE.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



