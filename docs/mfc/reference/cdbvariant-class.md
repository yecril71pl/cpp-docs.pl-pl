---
title: "Cdbvariant — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
dev_langs: C++
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71b19df1d89d07b578156e46a2915bdcd5c70004
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdbvariant-class"></a>Cdbvariant — klasa
Reprezentuje typ danych variant dla klas MFC ODBC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDBVariant  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDBVariant::CDBVariant](#cdbvariant)|Konstruuje `CDBVariant` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDBVariant::Clear](#clear)|Czyści `CDBVariant` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDBVariant::m_dwType](#m_dwtype)|Zawiera typ danych obecnie przechowywanej wartości. Typ `DWORD`.|  
  
### <a name="public-union-members"></a>Publicznych elementów członkowskich Unii  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDBVariant::m_boolVal](#m_boolval)|Zawiera wartość typu **BOOL**.|  
|[CDBVariant::m_chVal](#m_chval)|Zawiera wartość typu `unsigned char`.|  
|[CDBVariant::m_dblVal](#m_dblval)|Zawiera wartość typu **podwójne**.|  
|[CDBVariant::m_fltVal](#m_fltval)|Zawiera wartość typu **float**.|  
|[CDBVariant::m_iVal](#m_ival)|Zawiera wartość typu **krótki**.|  
|[CDBVariant::m_lVal](#m_lval)|Zawiera wartość typu **długi**.|  
|[CDBVariant::m_pbinary](#m_pbinary)|Zawiera wskaźnik do obiektu typu `CLongBinary`.|  
|[CDBVariant::m_pdate](#m_pdate)|Zawiera wskaźnik do obiektu typu **TIMESTAMP_STRUCT**.|  
|[CDBVariant::m_pstring](#m_pstring)|Zawiera wskaźnik do obiektu typu `CString`.|  
|[CDBVariant::m_pstringA](#m_pstringa)|Przechowuje wskaźnik do ASCII [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.|  
|[CDBVariant::m_pstringW](#m_pstringw)|Przechowuje wskaźnik do szerokiej [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CDBVariant`nie ma klasy podstawowej.  
  
 `CDBVariant`przypomina [COleVariant](../../mfc/reference/colevariant-class.md); jednak `CDBVariant` nie używa OLE. `CDBVariant`Służy do przechowywania wartości, nie martwiąc się o typ danych wartości. `CDBVariant`śledzi bieżącą wartość, który jest przechowywany w Unii typ danych.  
  
 Klasa [crecordset —](../../mfc/reference/crecordset-class.md) korzysta z `CDBVariant` obiektów w trzech funkcji elementów członkowskich: `GetFieldValue`, `GetBookmark`, i `SetBookmark`. Na przykład `GetFieldValue` umożliwia dynamicznie pobrać dane w kolumnie. Ponieważ typ danych kolumny nie może być znane w czasie wykonywania, `GetFieldValue` używa `CDBVariant` obiektu do przechowywania danych w kolumnie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDBVariant`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="cdbvariant"></a>CDBVariant::CDBVariant  
 Tworzy wartość NULL `CDBVariant` obiektu.  
  
```  
CDBVariant();
```  
  
### <a name="remarks"></a>Uwagi  
 Ustawia [m_dwType](#m_dwtype) element członkowski danych do **DBVT_NULL**.  
  
##  <a name="clear"></a>CDBVariant::Clear  
 Wywołanie tej funkcji Członkowskich, aby wyczyścić `CDBVariant` obiektu.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość [m_dwType](#m_dwtype) elementu członkowskiego danych jest **DBVT_DATE**, **DBVT_STRING**, lub **DBVT_BINARY**, **wyczyść**zwalnia pamięć skojarzone z danym elementem Unii wskaźnika. **Wyczyść** ustawia `m_dwType` do **DBVT_NULL**.  
  
 `CDBVariant` Wywołania destruktora **wyczyść**.  
  
##  <a name="m_boolval"></a>CDBVariant::m_boolVal  
 Przechowuje wartość typu **BOOL**.  
  
### <a name="remarks"></a>Uwagi  
 **M_boolVal** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_boolVal**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_BOOL**, następnie **m_boolVal** będzie zawierać prawidłową wartość; w przeciwnym razie dostęp do **m_boolVal** utworzy niewiarygodne wyniki.  
  
##  <a name="m_chval"></a>CDBVariant::m_chVal  
 Przechowuje wartość typu `unsigned char`.  
  
### <a name="remarks"></a>Uwagi  
 **M_chVal** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_chVal**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_UCHAR**, następnie **m_chVal** zawiera prawidłową wartość; w przeciwnym razie dostęp do **m_chVal** utworzy niewiarygodne wyniki.  
  
##  <a name="m_dblval"></a>CDBVariant::m_dblVal  
 Przechowuje wartość typu **podwójne**.  
  
### <a name="remarks"></a>Uwagi  
 **M_dblVal** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_dblVal**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_DOUBLE**, następnie **m_dblVal** zawiera prawidłową wartość; w przeciwnym razie dostęp do **m_dblVal** utworzy niewiarygodne wyniki.  
  
##  <a name="m_dwtype"></a>CDBVariant::m_dwType  
 Ten element członkowski danych zawiera typ danych dla wartości, który jest obecnie przechowywanych w `CDBVariant` element członkowski danych związku obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Przed uzyskaniem dostępu do tego Unii, należy sprawdzić wartość `m_dwType` w celu ustalenia, który element członkowski danych związku do uzyskania dostępu. W poniższej tabeli przedstawiono możliwe wartości `m_dwType` i odpowiedni element członkowski danych związku.  
  
|m_dwType|Element członkowski danych związku|  
|---------------|-----------------------|  
|**DBVT_NULL**|Nie elementu członkowskiego typu union jest prawidłowa dla dostępu.|  
|**DBVT_BOOL**|[m_boolVal](#m_boolval)|  
|**DBVT_UCHAR**|[m_chVal](#m_chval)|  
|**DBVT_SHORT**|[m_iVal](#m_ival)|  
|**DBVT_LONG**|[m_lVal](#m_lval)|  
|**DBVT_SINGLE**|[m_fltVal](#m_fltval)|  
|**DBVT_DOUBLE**|[m_dblVal](#m_dblval)|  
|**DBVT_DATE**|[m_pdate](#m_pdate)|  
|**DBVT_STRING**|[m_pstring](#m_pstring)|  
|**DBVT_BINARY**|[m_pbinary](#m_pbinary)|  
|**DBVT_ASTRING**|[m_pstringA](#m_pstringa)|  
|**DBVT_WSTRING**|[m_pstringW](#m_pstringw)|  
  
##  <a name="m_fltval"></a>CDBVariant::m_fltVal  
 Przechowuje wartość typu **float**.  
  
### <a name="remarks"></a>Uwagi  
 **M_fltVal** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_fltVal**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_SINGLE**, następnie **m_fltVal** zawiera prawidłową wartość; w przeciwnym razie dostęp do **m_fltVal** utworzy niewiarygodne wyniki.  
  
##  <a name="m_ival"></a>CDBVariant::m_iVal  
 Przechowuje wartość typu **krótki**.  
  
### <a name="remarks"></a>Uwagi  
 **M_iVal** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_iVal**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_SHORT**, następnie **m_iVal** zawiera prawidłową wartość; w przeciwnym razie dostęp do **m_iVal** utworzy niewiarygodne wyniki.  
  
##  <a name="m_lval"></a>CDBVariant::m_lVal  
 Przechowuje wartość typu **długi**.  
  
### <a name="remarks"></a>Uwagi  
 **M_lVal** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_lVal**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_LONG**, następnie **m_lVal** zawiera prawidłową wartość; w przeciwnym razie dostęp do **m_lVal** utworzy niewiarygodne wyniki.  
  
##  <a name="m_pbinary"></a>CDBVariant::m_pbinary  
 Przechowuje wskaźnik do obiektu typu [clongbinary —](../../mfc/reference/clongbinary-class.md).  
  
### <a name="remarks"></a>Uwagi  
 **M_pbinary** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_pbinary**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_BINARY**, następnie **m_pbinary** zawiera nieprawidłowy wskaźnik; w przeciwnym razie dostęp do **m_pbinary** utworzy niewiarygodne wyniki.  
  
##  <a name="m_pdate"></a>CDBVariant::m_pdate  
 Przechowuje wskaźnik do obiektu typu **TIMESTAMP_STRUCT**.  
  
### <a name="remarks"></a>Uwagi  
 **M_pdate** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_pdate**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_DATE**, następnie **m_pdate** zawiera nieprawidłowy wskaźnik; w przeciwnym razie dostęp do **m_pdate** utworzy niewiarygodne wyniki.  
  
 Aby uzyskać więcej informacji na temat **TIMESTAMP_STRUCT** typ danych, zobacz temat [typy danych C](https://msdn.microsoft.com/library/ms714556.aspx) z dodatkiem D *Podręcznik programisty ODBC* w zestawie Windows SDK.  
  
##  <a name="m_pstring"></a>CDBVariant::m_pstring  
 Przechowuje wskaźnik do obiektu typu [cstring —](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Uwagi  
 **M_pstring** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_pstring**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_STRING**, następnie **m_pstring** zawiera nieprawidłowy wskaźnik; w przeciwnym razie dostęp do **m_pstring** utworzy niewiarygodne wyniki.  
  
##  <a name="m_pstringa"></a>CDBVariant::m_pstringA  
 Przechowuje wskaźnik do ASCII [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 **M_pstringA** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_pstringA**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_ASTRING**, następnie **m_pstringA** zawiera nieprawidłowy wskaźnik; w przeciwnym razie dostęp do **m_pstringA** utworzy niewiarygodne wyniki.  
  
##  <a name="m_pstringw"></a>CDBVariant::m_pstringW  
 Przechowuje wskaźnik do szerokiej [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 **M_pstringW** element członkowski danych należy do Unii. Przed uzyskaniem dostępu do **m_pstringW**, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono **DBVT_WSTRING**, następnie **m_pstringW** zawiera nieprawidłowy wskaźnik; w przeciwnym razie dostęp do **m_pstringW** utworzy niewiarygodne wyniki.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)
