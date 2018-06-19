---
title: Clongbinary — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
dev_langs:
- C++
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7030fdcb59166c0e70a7b2c2471273c913fe459
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368023"
---
# <a name="clongbinary-class"></a>Clongbinary — klasa
Upraszcza pracy z obiektami bardzo dużych danych binarnych (często nazywane obiektami lub "duże obiekty binarne") w bazie danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CLongBinary : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLongBinary::CLongBinary](#clongbinary)|Konstruuje `CLongBinary` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Zawiera rzeczywisty rozmiar w bajtach obiektu danych, których dojścia jest przechowywany w `m_hData`.|  
|[CLongBinary::m_hData](#m_hdata)|Zawiera Windows `HGLOBAL` uchwyt do obiektu rzeczywisty obraz.|  
  
## <a name="remarks"></a>Uwagi  
 Na przykład pola rekordu w tabeli SQL może zawierać reprezentujący obraz mapy bitowej. A `CLongBinary` obiekt przechowuje takiego obiektu i przechowuje informacje o jego rozmiaru.  
  
> [!NOTE]
>  Ogólnie rzecz biorąc, jest lepsze postępowanie teraz [CByteArray](../../mfc/reference/cbytearray-class.md) w połączeniu z [dfx_binary —](record-field-exchange-functions.md#dfx_binary) funkcji. Można nadal używać `CLongBinary`, ale na ogół `CByteArray` udostępnia więcej funkcji w obszarze Win32, ponieważ nie istnieje już limit rozmiaru napotkano z 16-bitowych `CByteArray`. Ta informacja ma zastosowanie do programowania za pomocą obiektów DAO (Data Access), a także otwarte połączenie bazy danych (ODBC).  
  
 Aby użyć `CLongBinary` obiektu, deklaruje elementu członkowskiego danych pola typu `CLongBinary` w klasie zestawu rekordów. Ten element członkowski zostanie osadzony elementu członkowskiego klasy zestawu rekordów i utworzone w sytuacji, gdy jest utworzony zestaw rekordów. Po `CLongBinary` obiekt jest tworzony, mechanizmu pól rekordów (RFX) programu exchange ładuje obiekt danych z polem bieżącego rekordu w źródle danych i przechowuje wstecz do rekordu podczas aktualizacji rekordu. RFX kwerendy źródła danych dla rozmiaru dużego obiektu binarnego, przydziela magazynu (za pośrednictwem `CLongBinary` obiektu `m_hData` elementu członkowskiego danych) i przechowuje `HGLOBAL` obsługi z danymi w `m_hData`. RFX przechowuje także rzeczywisty rozmiar obiektu danych w `m_dwDataLength` element członkowski danych. Praca z danymi w obiekcie za pośrednictwem `m_hData`, przy użyciu tych samych metod, zazwyczaj jest używane do modyfikowania danych przechowywanych w systemie Windows `HGLOBAL` obsługi.  
  
 Gdy zniszczyć zestawu rekordów, osadzonego `CLongBinary` obiektu również zostanie zniszczony i zwalnia jego destruktora `HGLOBAL` obsługi danych.  
  
 Aby uzyskać więcej informacji o dużych obiektów i stosowania `CLongBinary`, zobacz artykuły [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md) i [zestaw rekordów: Praca z dużą elementów danych (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CLongBinary`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb_.h  
  
##  <a name="clongbinary"></a>  CLongBinary::CLongBinary  
 Konstruuje `CLongBinary` obiektu.  
  
```  
CLongBinary();
```  
  
##  <a name="m_dwdatalength"></a>  CLongBinary::m_dwDataLength  
 Przechowuje rzeczywisty rozmiar w bajtach danych przechowywanych w `HGLOBAL` obsługi w `m_hData`.  
  
```  
SQLULEN m_dwDataLength;  
```  
  
### <a name="remarks"></a>Uwagi  
 Rozmiar ten może być mniejszy niż rozmiar bloku pamięci przydzielona dla danych. Wywołanie Win32 [funkcja GLobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593) funkcji, aby pobrać przydzielony rozmiar.  
  
##  <a name="m_hdata"></a>  CLongBinary::m_hData  
 Przechowuje Windows `HGLOBAL` dojścia do danych rzeczywistych dużego obiektu binarnego.  
  
```  
HGLOBAL m_hData;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CRecordset](../../mfc/reference/crecordset-class.md)
