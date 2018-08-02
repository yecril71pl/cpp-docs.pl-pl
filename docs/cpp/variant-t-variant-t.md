---
title: _variant_t::_variant_t | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ef7551047449167ff60372da146618fbdc4e564
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464165"
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
**Microsoft Specific**  
  
 Konstruuje `_variant_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
_variant_t( ) throw( );  
  
_variant_t(  
   const VARIANT& varSrc   
);  
  
_variant_t(  
   const VARIANT* pVarSrc   
);  
  
_variant_t(  
   const _variant_t& var_t_Src   
);  
  
_variant_t(  
   VARIANT& varSrc,  
   bool fCopy   
);  
  
_variant_t(  
   short sSrc,  
   VARTYPE vtSrc = VT_I2   
);  
  
_variant_t(  
   long lSrc,  
   VARTYPE vtSrc = VT_I4   
);  
  
_variant_t(  
   float fltSrc   
) throw( );  
  
_variant_t(  
   double dblSrc,  
   VARTYPE vtSrc = VT_R8   
);  
  
_variant_t(  
   const CY& cySrc   
) throw( );  
  
_variant_t(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t(  
   const wchar_t *wstrSrc   
);  
  
_variant_t(  
   const char* strSrc   
);  
  
_variant_t(  
   IDispatch* pDispSrc,  
   bool fAddRef = true   
) throw( );  
  
_variant_t(  
   bool bSrc   
) throw( );  
  
_variant_t(  
   IUnknown* pIUknownSrc,  
   bool fAddRef = true   
) throw( );  
  
_variant_t(  
   const DECIMAL& decSrc   
) throw( );  
  
_variant_t(  
   BYTE bSrc   
) throw( );  
  
variant_t(  
   char cSrc  
) throw();  
  
_variant_t(  
   unsigned short usSrc  
) throw();  
  
_variant_t(  
   unsigned long ulSrc  
) throw();  
  
_variant_t(  
   int iSrc  
) throw();  
  
_variant_t(  
   unsigned int uiSrc  
) throw();  
  
_variant_t(  
   __int64 i8Src  
) throw();  
  
_variant_t(  
   unsigned __int64 ui8Src  
) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A `VARIANT` obiektu do skopiowania w nowe `_variant_t` obiektu.  
  
 *pVarSrc*  
 Wskaźnik do `VARIANT` obiektu do skopiowania w nowe `_variant_t` obiektu.  
  
 *var_t_Src*  
 A `_variant_t` obiektu do skopiowania w nowe `_variant_t` obiektu.  
  
 *fCopy*  
 Jeśli **false**, podane `VARIANT` obiekt jest dołączony do nowej `_variant_t` obiektu bez wprowadzania nowych Kopiuj w oparciu o `VariantCopy`.  
  
 *Kod, sSrc*  
 Wartość całkowitą do skopiowania w nowe `_variant_t` obiektu.  
  
 *vtSrc*  
 `VARTYPE` Dla nowego `_variant_t` obiektu.  
  
 *fltSrc, dblSrc*  
 Wartość liczbową do skopiowania w nowe `_variant_t` obiektu.  
  
 *cySrc*  
 A `CY` obiektu do skopiowania w nowe `_variant_t` obiektu.  
  
 *bstrSrc*  
 A `_bstr_t` obiektu do skopiowania w nowe `_variant_t` obiektu.  
  
 *strSrc, wstrSrc*  
 Ciąg do skopiowania w nowe `_variant_t` obiektu.  
  
 *bSrc*  
 A **bool** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *pIUknownSrc*  
 Wskaźnik interfejsu COM do obiektu VT_UNKNOWN celu są umieszczane na nowym `_variant_t` obiektu.  
  
 *pDispSrc*  
 Wskaźnik interfejsu COM do obiektu VT_DISPATCH celu są umieszczane na nowym `_variant_t` obiektu.  
  
 *decSrc*  
 A `DECIMAL` wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *bSrc*  
 A `BYTE` wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *cSrc*  
 A **char** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *usSrc*  
 A **typ unsigned short** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *ulSrc*  
 A **unsigned long** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *Kod*  
 **Int** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *uiSrc*  
 **Unsigned int** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *i8Src*  
 **__Int64** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
 *ui8Src*  
 **Unsigned __int64** wartość do skopiowania w nowe `_variant_t` obiektu.  
  
## <a name="remarks"></a>Uwagi  
  
-   **_variant_t — ()** tworzy pustą `_variant_t` obiektu `VT_EMPTY`.  
  
-   **_variant_t — (WARIANTU &***varSrc***)** tworzy `_variant_t` obiektu na podstawie kopii `VARIANT` obiektu.     Typ wariantu są zachowywane.  
  
-   **_variant_t — (WARIANTU\****pVarSrc***)** tworzy `_variant_t` obiektu na podstawie kopii `VARIANT` obiektu.     Typ wariantu są zachowywane.  
  
-   **_variant_t — (_variant_t &***var_t_Src***)** tworzy `_variant_t` obiektu z innego `_variant_t` obiektu.     Typ wariantu są zachowywane.  
  
-   **_variant_t — (WARIANTU &***varSrc* **, bool**`fCopy`**)** tworzy `_variant_t` obiektu z istniejącego `VARIANT` obiekt.       Jeśli *fCopy* jest **false**, **VARIANT** obiekt jest dołączony do nowego obiektu bez tworzenia kopii.  
  
-   **_variant_t — (krótki***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** tworzy `_variant_t` obiektu typu VT_I2 lub VT_BOOL, z **krótki** wartość całkowitą.       Inne `VARTYPE` powoduje błąd E_INVALIDARG.  
  
-   **_variant_t — (long** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** tworzy `_variant_t` obiektu o typie, VT_I4, VT_BOOL. lub VT_ERROR z **długi**  wartość całkowitą.       Inne `VARTYPE` powoduje błąd E_INVALIDARG.  
  
-   **_variant_t — (float**`fltSrc`**)** tworzy `_variant_t` obiektu typu VT_R4 z **float** wartość liczbową.      
  
-   **_variant_t — (podwójny** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** tworzy `_variant_t` obiektu typu VT_R8 lub VT_DATE z **podwójnejprecyzji** wartość liczbową.       Inne `VARTYPE` powoduje błąd E_INVALIDARG.  
  
-   **_variant_t — (CY &**`cySrc`**)** tworzy `_variant_t` typu VT_CY z `CY` obiektu.      
  
-   **_variant_t — (_bstr_t &**`bstrSrc`**)** tworzy `_variant_t` typu VT_BSTR z `_bstr_t` obiektu.     Nowy `BSTR` jest przydzielony.  
  
-   **_variant_t — (wchar_t \***  *wstrSrc***)** tworzy `_variant_t` obiektu typu VT_BSTR z ciągu Unicode.   Nowy `BSTR` jest przydzielony.  
  
-   **_variant_t — (char\***`strSrc`**)** tworzy `_variant_t` obiektu typu VT_BSTR z ciągu.     Nowy `BSTR` jest przydzielony.  
  
-   **_variant_t — (wartość logiczna**`bSrc`**)** tworzy `_variant_t` typu VT_BOOL, z **bool** wartość.      
  
-   **_variant_t — (IUnknown\***  `pIUknownSrc` **, bool**`fAddRef`**= true)** tworzy `_variant_t` obiektu typu VT_UNKNOWN ze wskaźnika interfejsu COM .       Jeśli `fAddRef` jest **true**, następnie `AddRef` jest wywoływana we wskaźniku interfejsu podany w celu dopasowania wywołania do `Release` , nastąpi po `_variant_t` niszczony jest obiekt. Aby wywołać to `Release` na wskaźnik interfejsu podany. Jeśli `fAddRef` jest **false**, ten konstruktor przejmuje na własność wskaźnika interfejsu podany; nie należy wywoływać metody `Release` na wskaźnik interfejsu podany.  
  
-   **_variant_t — (IDispatch\***  `pDispSrc` **, bool**`fAddRef`**= true)** tworzy `_variant_t` obiektu typu VT_DISPATCH za pomocą interfejsu COM wskaźnik.       Jeśli `fAddRef` jest **true**, następnie `AddRef` jest wywoływana we wskaźniku interfejsu podany w celu dopasowania wywołania do `Release` , nastąpi po `_variant_t` niszczony jest obiekt. Aby wywołać to `Release` na wskaźnik interfejsu podany. Jeśli `fAddRef` jest **false**, ten konstruktor przejmuje na własność wskaźnika interfejsu podany; nie należy wywoływać metody `Release` na wskaźnik interfejsu podany.  
  
-   **_variant_t — (dziesiętna &**`decSrc`**)** tworzy `_variant_t` typu VT_DECIMAL z `DECIMAL` wartości.      
  
-   **_variant_t — (BAJTÓW**`bSrc`**)** tworzy `_variant_t` obiektu typu `VT_UI1` z `BYTE` wartości.      
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_variant_t, klasa](../cpp/variant-t-class.md)