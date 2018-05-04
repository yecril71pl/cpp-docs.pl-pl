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
ms.openlocfilehash: 59ec19adc66a72a7c98772db99aaab3eee4e3b2c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 A **VARIANT** obiekt ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *pVarSrc*  
 Wskaźnik do **VARIANT** obiekt ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *var_t_Src*  
 A `_variant_t` obiekt ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `fCopy`  
 W przypadku wartości FAŁSZ podane **VARIANT** obiekt jest dołączony do nowej `_variant_t` obiektu bez tworzenia nowej kopii przez **VariantCopy**.  
  
 *Kod, sSrc*  
 Wartość całkowita ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `vtSrc`  
 **VARTYPE** nowego `_variant_t` obiektu.  
  
 *fltSrc, dblSrc*  
 Wartość liczbową można skopiować do nowego `_variant_t` obiektu.  
  
 `cySrc`  
 A **CY** obiekt ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `bstrSrc`  
 A `_bstr_t` obiekt ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *strSrc, wstrSrc*  
 Ciąg, który ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `bSrc`  
 A `bool` wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `pIUknownSrc`  
 Wskaźnika interfejsu COM do **VT_UNKNOWN** obiektu są umieszczane w nowej `_variant_t` obiektu.  
  
 `pDispSrc`  
 Wskaźnika interfejsu COM do **VT_DISPATCH** obiektu są umieszczane w nowej `_variant_t` obiektu.  
  
 `decSrc`  
 A **DZIESIĘTNĄ** wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `bSrc`  
 A **BAJTÓW** wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `cSrc`  
 A `char` wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *usSrc*  
 A **niepodpisane krótko** wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *ulSrc*  
 A `unsigned long` wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 `iSrc`  
 `int` Wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *uiSrc*  
 `unsigned int` Wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *i8Src*  
 __**Int64** wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
 *ui8Src*  
 **Niepodpisane __int64** wartość ma zostać skopiowany do nowego `_variant_t` obiektu.  
  
## <a name="remarks"></a>Uwagi  
  
-   **_variant_t ()** tworzy pustą `_variant_t` obiektu `VT_EMPTY`.  
  
-   **_variant_t — (VARIANT &***varSrc***)** tworzy `_variant_t` obiektu z kopii **VARIANT** obiektu. Typ wariantu są zachowywane.  
  
-   **_variant_t — (VARIANT\****pVarSrc***)** tworzy `_variant_t` obiektu z kopii **VARIANT** obiektu. Typ wariantu są zachowywane.  
  
-   **_variant_t — (_variant_t &***var_t_Src***)** tworzy `_variant_t` obiektu z innego `_variant_t` obiektu. Typ wariantu są zachowywane.  
  
-   **_variant_t — (VARIANT &***varSrc* **, bool**`fCopy`**)** tworzy `_variant_t` obiektu z istniejącego  **VARIANT** obiektu. Jeśli `fCopy` jest **false**, **VARIANT** obiekt jest dołączony do nowego obiektu bez tworzenia kopii.  
  
-   **_variant_t — (krótka***sSrc* **, VARTYPE**`vtSrc`**= VT_I2)** tworzy `_variant_t` obiektu typu `VT_I2` lub `VT_BOOL` z **krótki** wartości całkowitej. Inne **VARTYPE** powoduje `E_INVALIDARG` błędu.  
  
-   **_variant_t — (długi** `lSrc` **, VARTYPE**`vtSrc`**= VT_I4)** tworzy `_variant_t` typu obiektu `VT_I4`, `VT_BOOL`, lub `VT_ERROR`z **długi** wartości całkowitej. Inne **VARTYPE** powoduje `E_INVALIDARG` błędu.  
  
-   **_variant_t — (float**`fltSrc`**)** tworzy `_variant_t` typu obiektu `VT_R4` z **float** wartość liczbową.  
  
-   **_variant_t — (dwa razy** `dblSrc` **, VARTYPE**`vtSrc`**= VT_R8)** tworzy `_variant_t` typu obiektu `VT_R8` lub `VT_DATE` z **podwójne** wartość liczbową. Inne **VARTYPE** powoduje `E_INVALIDARG` błędu.  
  
-   **_variant_t — (CY &**`cySrc`**)** tworzy `_variant_t` typu obiektu `VT_CY` z **CY** obiektu.  
  
-   **_variant_t — (_bstr_t &**`bstrSrc`**)** tworzy `_variant_t` typu obiektu `VT_BSTR` z `_bstr_t` obiektu. Nowy `BSTR` został przydzielony.  
  
-   **_variant_t — (wchar_t \***  *wstrSrc***)** tworzy `_variant_t` obiektu typu `VT_BSTR` z ciągiem Unicode. Nowy `BSTR` został przydzielony.  
  
-   **_variant_t — (char\***`strSrc`**)** tworzy `_variant_t` typu obiektu `VT_BSTR` z ciągu. Nowy `BSTR` został przydzielony.  
  
-   **_variant_t (wartość logiczna**`bSrc`**)** tworzy `_variant_t` typu obiektu `VT_BOOL` z `bool` wartości.  
  
-   **_variant_t — (IUnknown\***  `pIUknownSrc` **, bool**`fAddRef`**= true)** tworzy `_variant_t` typu obiektu **VT_UNKNOWN** ze wskaźnika interfejsu COM. Jeśli `fAddRef` jest **true**, następnie `AddRef` jest wywoływana na wskaźniku interfejs dostarczony w celu dopasowania wywołania do **wersji** który nastąpi po `_variant_t` obiekt zostanie zniszczony. Aby wywołać jest **wersji** na wskaźnik interfejsu podany. Jeśli `fAddRef` jest **false**, ten konstruktor przejmuje wskaźnika interfejsu podany; nie należy wywoływać **wersji** na wskaźnik interfejsu podany.  
  
-   **_variant_t — (IDispatch\***  `pDispSrc` **, bool**`fAddRef`**= true)** tworzy `_variant_t` typu obiektu **VT_DISPATCH** ze wskaźnika interfejsu COM. Jeśli `fAddRef` jest **true**, następnie `AddRef` jest wywoływana na wskaźniku interfejs dostarczony w celu dopasowania wywołania do **wersji** który nastąpi po `_variant_t` obiekt zostanie zniszczony. Aby wywołać jest **wersji** na wskaźnik interfejsu podany. Jeśli **fAddRef** jest false, ten konstruktor przejmuje wskaźnika interfejsu podany; nie należy wywoływać **wersji** na wskaźnik interfejsu podany.  
  
-   **_variant_t — (dziesiętne &**`decSrc`**)** tworzy `_variant_t` typu obiektu **VT_DECIMAL** z **DZIESIĘTNĄ** wartość.  
  
-   **_variant_t — (BYTE**`bSrc`**)** tworzy `_variant_t` typu obiektu `VT_UI1` z **BAJTÓW** wartość.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)