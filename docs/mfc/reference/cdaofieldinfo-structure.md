---
title: Cdaofieldinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d08dd9d877d8872c5c8a930e84ae0496c745709
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo — Struktura
`CDaoFieldInfo` Struktura zawiera informacje dotyczące obiektu pola zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoFieldInfo  
{  
    CString m_strName;           // Primary  
    short m_nType;               // Primary  
    long m_lSize;                // Primary  
    long m_lAttributes;          // Primary  
    short m_nOrdinalPosition;    // Secondary  
    BOOL m_bRequired;            // Secondary  
    BOOL m_bAllowZeroLength;     // Secondary  
    long m_lCollatingOrder;      // Secondary  
    CString m_strForeignName;    // Secondary  
    CString m_strSourceField;    // Secondary  
    CString m_strSourceTable;    // Secondary  
    CString m_strValidationRule; // All  
    CString m_strValidationText; // All  
    CString m_strDefaultValue;   // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Unikatowej nazwy obiektu pola. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 `m_nType`  
 Wartość, która określa typ danych pola. Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w pomocy DAO. Wartość tej właściwości może być jedną z następujących czynności:  
  
- **dbBoolean** tak/nie, taka sama jak **TRUE**/**FALSE**  
  
- **dbByte** bajtów  
  
- **dbInteger** krótki  
  
- **dbLong** długa  
  
- **dbCurrency** waluty; Zobacz klasy MFC [COleCurrency](../../mfc/reference/colecurrency-class.md)  
  
- **dbSingle** pojedynczego  
  
- **dbDouble** podwójne  
  
- **dbDate** daty/godziny; Zobacz klasy MFC [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)  
  
- **dbText** tekst; Zobacz klasy MFC [cstring —](../../atl-mfc-shared/reference/cstringt-class.md)  
  
- **dbLongBinary** Long Binary (obiekt OLE); można użyć klasy MFC [CByteArray](../../mfc/reference/cbytearray-class.md) zamiast klasy `CLongBinary` jako `CByteArray` jest bardziej zaawansowane funkcje i łatwiejsze do użycia.  
  
- **dbMemo** Memo; Zobacz klasy MFC `CString`  
  
- **dbGUID** A Unikatowy identyfikator/Uniwersalnie unikatowy identyfikator globalny używany z zdalnych wywołań procedur. Aby uzyskać więcej informacji zobacz temat "Właściwość Type" w pomocy DAO.  
  
> [!NOTE]
>  Nie używaj danych typu ciąg dla danych binarnych. Powoduje to dane przekazywane do warstwy tłumaczenia Unicode/ANSI, co powoduje tłumaczenie zwiększone obciążenie i prawdopodobnie nieoczekiwany.  
  
 *m_lSize*  
 Wartość, która określa maksymalny rozmiar w bajtach obiektu pola DAO, który zawiera tekst lub stały rozmiar pola obiektu, który zawiera wartości tekstowe lub liczbowe. Aby uzyskać więcej informacji zobacz temat "Rozmiar Property" w pomocy DAO. Rozmiary może być jedną z następujących wartości:  
  
|Typ|Rozmiar (w bajtach)|Opis|  
|----------|--------------------|-----------------|  
|**dbBoolean**|1 bajt|Tak/nie (tak samo jak PRAWDA/FAŁSZ)|  
|**dbByte**|1|Byte|  
|**dbInteger**|2|Liczba całkowita|  
|**dbLong**|4|długa|  
|**dbCurrency**|8|Currency ([COleCurrency](../../mfc/reference/colecurrency-class.md))|  
|**dbSingle**|4|Single|  
|**dbDouble**|8|Double|  
|**dbDate**|8|Data/Godzina ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|  
|**dbText**|1 - 255|Tekst ([cstring —](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbLongBinary**|0|Długie pliku binarnego (obiekt OLE; [CByteArray](../../mfc/reference/cbytearray-class.md); Użyj zamiast `CLongBinary`)|  
|**dbMemo**|0|Memo ([cstring —](../../atl-mfc-shared/reference/cstringt-class.md))|  
|**dbGUID**|16|Globalnie unikatowy identyfikator/Uniwersalnie unikatowy identyfikator używany ze zdalnych wywołań procedur.|  
  
 `m_lAttributes`  
 Określa charakterystykę obiektu pola zawarty w tabledef, zestawu rekordów, querydef lub obiekt indeksu. Wartość zwracana może być sumę te stałe utworzone za pomocą języka C++ Alternatywy (**&#124;**) — operator:  
  
- **dbFixedField** rozmiar pola jest stała (domyślnie dla pól liczbowych).  
  
- **dbVariableField** rozmiar pola jest zmienna (tylko pola tekstowe).  
  
- **dbAutoIncrField** wartości pola dla nowych rekordów jest automatycznie zwiększany do unikatowy długich liczb całkowitych, nie można jej zmienić. Obsługiwane tylko dla tabel bazy danych programu Microsoft Jet.  
  
- **dbUpdatableField** można zmienić wartość pola.  
  
- **dbDescending** sortowania pola w malejącej (Z - A lub 100-0) zamówienia (dotyczy tylko do pól obiektu w kolekcji pól obiektu indeksu; w MFC, indeks obiekty się znajdują się w obiektach tabledef). W przypadku pominięcia tego stała, pole są posortowane w kolejności rosnącej (A - Z lub 0 - 100) zamówienia (ustawienie domyślne).  
  
 Podczas sprawdzania ustawienie tej właściwości, można użyć języka C++ bitowe- i — operator (**&**) do przetestowania określonego atrybutu. Podczas ustawiania wiele atrybutów, można je połączyć, łącząc odpowiednie stałe z bitowego OR (**&#124;**) operatora. Aby uzyskać więcej informacji zobacz temat "Właściwość Attributes" w pomocy DAO.  
  
 *m_nOrdinalPosition*  
 Wartość, która określa kolejności numerycznej, w którym mają być reprezentowane przez obiekt DAO pola mają być wyświetlane względem innych pól pola. Można ustawić tę właściwość z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield). Aby uzyskać więcej informacji zobacz temat "OrdinalPosition Property" w pomocy DAO.  
  
 `m_bRequired`  
 Wskazuje, czy obiekt DAO pole wymaga wartości innej niż Null. Jeśli ta właściwość jest **TRUE**, pole nie obsługuje wartości Null. Jeśli wymagane jest ustawiona na **FALSE**, pole może zawierać wartości Null, a także wartości, które spełniają warunki określony przez ustawienia właściwości AllowZeroLength i ValidationRule. Aby uzyskać więcej informacji zobacz temat "Wymagana właściwość" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_bAllowZeroLength*  
 Wskazuje, czy ciąg pusty ("") jest prawidłową wartością pola obiektu DAO zawierającą dane typu tekst lub Nota. Jeśli ta właściwość jest **TRUE**, ciąg pusty jest prawidłową wartością. Tę właściwość można ustawić, **FALSE** aby upewnić się, że nie można użyj pustego ciągu można ustawić wartości pola. Aby uzyskać więcej informacji zobacz temat "AllowZeroLength Property" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_lCollatingOrder`  
 Określa sekwencję kolejności sortowania w tekście do porównania ciągów i sortowania. Aby uzyskać więcej informacji zobacz temat "Dostosowywanie systemu Windows rejestru ustawienia dla Data Access" w pomocy DAO. Aby uzyskać listę możliwych wartości zwracane, zobacz **m_lCollatingOrder** członkiem [cdaodatabaseinfo —](../../mfc/reference/cdaodatabaseinfo-structure.md) struktury. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_strForeignName`  
 Wartość, która w relacji, określa nazwę pola obiektu DAO w obcy tabeli, która odpowiada polu w tabeli podstawowej. Aby uzyskać więcej informacji zobacz temat "ForeignName Property" w pomocy DAO.  
  
 *m_strSourceField*  
 Wskazuje nazwę pola, które jest oryginalne źródło danych dla obiekt pola DAO zawarty w tabledef, rekordów lub obiektu querydef. Ta właściwość wskazuje oryginalna nazwa pola powiązane z obiektem pola. Na przykład można użyć tej właściwości do określenia oryginalne źródło danych w polu zapytania, którego nazwa jest związana z nazwa pola w tabeli podstawowej. Aby uzyskać więcej informacji zobacz temat "SourceField, właściwości elementu SourceTable" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_strSourceTable*  
 Wskazuje nazwę tabeli, która jest oryginalne źródło danych dla obiekt pola DAO zawarty w tabledef, rekordów lub obiektu querydef. Ta właściwość wskazuje skojarzone z obiektem pola oryginalnej nazwy tabeli. Na przykład można użyć tej właściwości do określenia oryginalne źródło danych w polu zapytania, którego nazwa jest związana z nazwa pola w tabeli podstawowej. Aby uzyskać więcej informacji zobacz temat "SourceField, właściwości elementu SourceTable" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 `m_strValidationRule`  
 Wartość, która weryfikuje dane w polu, w jakiej jest zmieniane ani dodawane do tabeli. Aby uzyskać więcej informacji zobacz temat "ValidationRule Property" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 Powiązane informacje na temat tabledefs — zobacz **m_strValidationRule** członkiem [cdaotabledefinfo —](../../mfc/reference/cdaotabledefinfo-structure.md) struktury.  
  
 `m_strValidationText`  
 Wartość, która określa tekst wiadomości, które będą wyświetlane w aplikacji, jeśli wartość pola obiektu DAO nie spełnia warunków reguły sprawdzania poprawności określonego przez ustawienie właściwości ValidationRule. Aby uzyskać więcej informacji zobacz temat "Komunikat Property" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
 *m_strDefaultValue*  
 Wartość domyślna pola obiektu DAO. Po utworzeniu nowego rekordu ustawienie Właściwość DefaultValue jest wprowadzana automatycznie jako wartość dla pola. Aby uzyskać więcej informacji zobacz temat "Właściwość DefaultValue" w pomocy DAO. Można ustawić tej właściwości dla tabledef z [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield).  
  
## <a name="remarks"></a>Uwagi  
 Odwołania do podstawowej, pomocniczej i wszystkie powyższe wskazują, jak informacje zwracane przez `GetFieldInfo` funkcji Członkowskich w klasach [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo), i [ Cdaorecordset —](../../mfc/reference/cdaorecordset-class.md#getfieldinfo).  
  
 Pole obiekty nie są reprezentowane przez klasę MFC. Zamiast tego źródłowych MFC — obiekty z następujących klas obiektów DAO zawierać kolekcje obiektów pola: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md), i [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Te klasy dostarczyć funkcji elementów członkowskich na dostęp do niektórych poszczególne pola informacje, lub uzyskać dostępu do nich jednocześnie z `CDaoFieldInfo` obiektu przez wywołanie metody `GetFieldInfo` funkcji członkowskiej krawędzi zawierającego go obiektu.  
  
 Oprócz obsługi badania właściwości obiektu, można również użyć `CDaoFieldInfo` do utworzenia przy tworzeniu nowych pól w tabledef parametru wejściowego. Prostsze opcje są dostępne dla tego zadania, ale jeśli chcesz bardziej precyzyjną kontrolę, można użyć wersji [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) pobierającej `CDaoFieldInfo` parametru.  
  
 Informacje o pobrane przez `GetFieldInfo` funkcji członkowskiej (klasy, która zawiera pole) są przechowywane w `CDaoFieldInfo` struktury. Wywołanie `GetFieldInfo` funkcji członkowskiej klasy obiektu zawierającego, w których kolekcji pól obiektu pola są przechowywane. `CDaoFieldInfo` definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoFieldInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)   
 [CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)   
 [CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)

