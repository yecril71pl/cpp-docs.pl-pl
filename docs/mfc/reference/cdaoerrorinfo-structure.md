---
title: Cdaoerrorinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 787e9d5ac860e283d6eacc0f22b790a6196485f4
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335571"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo — Struktura
`CDaoErrorInfo` Struktura zawiera informacje dotyczące obiekt błędu zdefiniowany dla obiektów dostępu do danych (DAO).  
  
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
 Kod liczbowy błąd DAO. Zobacz temat "Możliwe do wychwycenia błędami dostępu do danych" w Pomocy programu DAO.  
  
 *m_strSource*  
 Nazwa obiektu lub aplikacji, który początkowo wygenerował błąd. Właściwość Source Określa ciąg reprezentujący obiekt, który oryginalnie błąd; wyrażenie jest zazwyczaj nazwy klasy obiektu. Aby uzyskać szczegółowe informacje zobacz temat "Właściwości Source" w Pomocy programu DAO.  
  
 *m_strDescription*  
 Opisowy ciąg skojarzony z błędem. Aby uzyskać szczegółowe informacje zobacz temat "Właściwość Description" w Pomocy programu DAO.  
  
 *m_strHelpFile*  
 W pełni kwalifikowana ścieżka do pliku Pomocy programu Microsoft Windows. Aby uzyskać szczegółowe informacje w temacie "Helpcontext —, HelpFile właściwości" w Pomocy programu DAO.  
  
 *m_lHelpContext*  
 Identyfikator kontekstu dla tematu w pliku Pomocy programu Microsoft Windows. Aby uzyskać szczegółowe informacje w temacie "Helpcontext —, HelpFile właściwości" w Pomocy programu DAO.  
  
## <a name="remarks"></a>Uwagi  
 MFC nie hermetyzuje DAO błąd obiektów w klasie. Zamiast tego [CDaoException](../../mfc/reference/cdaoexception-class.md) klasa zapewnia interfejs do uzyskiwania dostępu do kolekcji błędów zawarte w obiekt DAO `DBEngine` object, obiekt, który zawiera również wszystkie obszary robocze. Gdy operacja MFC DAO zgłosi `CDaoException` obiektu czy przechwytujesz, wypełnia MFC `CDaoErrorInfo` struktury i zapisuje go w obiekt wyjątku [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) elementu członkowskiego. (Jeśli wybierzesz wywoływanie obiektów DAO bezpośrednio, należy wywołać obiekt wyjątku [geterrorinfo —](../../mfc/reference/cdaoexception-class.md#geterrorinfo) funkcja elementu członkowskiego sobie, aby wypełnić `m_pErrorInfo`.)  
  
 Aby uzyskać więcej informacji na temat obsługi błędów DAO, zobacz artykuł [wyjątki: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md). Aby uzyskać powiązane informacje zobacz temat "Błąd do obiektu" w Pomocy programu DAO.  
  
 Informacje o pobrane przez [CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) funkcja członkowska jest przechowywany w `CDaoErrorInfo` struktury. Sprawdź [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) element członkowski danych z `CDaoException` obiekt, który catch w program obsługi wyjątków lub wywołanie `GetErrorInfo` z `CDaoException` obiekt, który jawnie utworzyć w celu sprawdzenia błędów, które mogą mieć wystąpiły bezpośrednie wywołanie interfejsów DAO. `CDaoErrorInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoErrorInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
