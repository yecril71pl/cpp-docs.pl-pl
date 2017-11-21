---
title: "Cdaoerrorinfo — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoErrorInfo
dev_langs: C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e3d7637bfd6247dee79df4716a3e638a49e36cbf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo — Struktura
`CDaoErrorInfo` Struktura zawiera informacje o obiektach błąd zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoErrorInfo  
{  
    long m_lErrorCode;  
    CString m_strSource;  
    CString m_strDescription;  
    CString m_strHelpFile;  
    long m_lHelpContext;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *m_lErrorCode*  
 Liczbowa kod błędu DAO. Zobacz temat "Przechwytywalny błędami dostępu do danych" w pomocy DAO.  
  
 *m_strSource*  
 Nazwa obiektu lub aplikacji, który pierwotnie wygenerował błąd. Właściwość Source Określa ciąg reprezentujący obiekt, który pierwotnie wygenerowany błąd; wyrażenie jest zwykle nazwa klasy obiektu. Aby uzyskać więcej informacji zobacz temat "Właściwości Source" w pomocy DAO.  
  
 *m_strDescription*  
 Ciąg opisujący skojarzony z błędem. Aby uzyskać więcej informacji zobacz temat "Opis właściwości" w pomocy DAO.  
  
 *m_strHelpFile*  
 Pełna ścieżka do pliku Pomocy systemu Windows. Aby uzyskać więcej informacji zobacz temat "HelpContext HelpFile właściwości" w pomocy DAO.  
  
 *m_lHelpContext*  
 Identyfikator kontekstu dla tematu w pliku Pomocy systemu Windows. Aby uzyskać więcej informacji zobacz temat "HelpContext HelpFile właściwości" w pomocy DAO.  
  
## <a name="remarks"></a>Uwagi  
 MFC nie hermetyzować DAO błąd obiektów w klasie. Zamiast tego [CDaoException](../../mfc/reference/cdaoexception-class.md) klasa zapewnia interfejs do uzyskiwania dostępu do kolekcji błędów zawarte w obiekt DAO **interfejsu** obiektu, obiekt zawierający wszystkie obszary robocze. Podczas operacji MFC DAO zgłasza `CDaoException` obiektów, że zostaną wychwycone, wypełnia MFC `CDaoErrorInfo` struktury i zapisuje go w obiekcie wyjątek [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) elementu członkowskiego. (Jeśli wybierzesz wywoływanie obiektów DAO bezpośrednio, należy wywołać obiekt wyjątku [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) funkcji członkowskiej samodzielnie, aby wypełnić `m_pErrorInfo`.)  
  
 Aby uzyskać więcej informacji na temat obsługi błędów DAO, zobacz artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md). Powiązane informacje zobacz temat "Błąd do obiektu" w pomocy DAO.  
  
 Informacje o pobrane przez [CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) funkcja członkowska jest przechowywany w `CDaoErrorInfo` struktury. Sprawdź [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) element członkowski danych z `CDaoException` obiekt, który efektywnej obsługi wyjątków lub wywołanie `GetErrorInfo` z `CDaoException` obiektu utworzonego jawnie Aby sprawdzić błędy, które mogą mieć Wystąpił podczas bezpośredniego wywoływania interfejsów DAO. `CDaoErrorInfo`definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoErrorInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
