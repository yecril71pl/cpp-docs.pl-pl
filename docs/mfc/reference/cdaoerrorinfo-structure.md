---
title: CDaoErrorInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: dd9610fce88c18ac42de81ed712492766ee705de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266014"
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

*m_lErrorCode*<br/>
Kod liczbowy błąd DAO. Zobacz temat "Możliwe do wychwycenia błędami dostępu do danych" w Pomocy programu DAO.

*m_strSource*<br/>
Nazwa obiektu lub aplikacji, który początkowo wygenerował błąd. Właściwość Source Określa ciąg reprezentujący obiekt, który oryginalnie błąd; wyrażenie jest zazwyczaj nazwy klasy obiektu. Aby uzyskać szczegółowe informacje zobacz temat "Właściwości Source" w Pomocy programu DAO.

*m_strDescription*<br/>
Opisowy ciąg skojarzony z błędem. Aby uzyskać szczegółowe informacje zobacz temat "Właściwość Description" w Pomocy programu DAO.

*m_strHelpFile*<br/>
W pełni kwalifikowana ścieżka do pliku Pomocy programu Microsoft Windows. Aby uzyskać szczegółowe informacje w temacie "Helpcontext —, HelpFile właściwości" w Pomocy programu DAO.

*m_lHelpContext*<br/>
Identyfikator kontekstu dla tematu w pliku Pomocy programu Microsoft Windows. Aby uzyskać szczegółowe informacje w temacie "Helpcontext —, HelpFile właściwości" w Pomocy programu DAO.

## <a name="remarks"></a>Uwagi

MFC nie hermetyzuje DAO błąd obiektów w klasie. Zamiast tego [CDaoException](../../mfc/reference/cdaoexception-class.md) klasa zapewnia interfejs do uzyskiwania dostępu do kolekcji błędów zawarte w obiekt DAO `DBEngine` object, obiekt, który zawiera również wszystkie obszary robocze. Gdy operacja MFC DAO zgłosi `CDaoException` obiektu czy przechwytujesz, wypełnia MFC `CDaoErrorInfo` struktury i zapisuje go w obiekt wyjątku [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) elementu członkowskiego. (Jeśli wybierzesz wywoływanie obiektów DAO bezpośrednio, należy wywołać obiekt wyjątku [geterrorinfo —](../../mfc/reference/cdaoexception-class.md#geterrorinfo) funkcja elementu członkowskiego sobie, aby wypełnić `m_pErrorInfo`.)

Aby uzyskać więcej informacji na temat obsługi błędów DAO, zobacz artykuł [wyjątków: Baza danych wyjątki](../../mfc/exceptions-database-exceptions.md). Aby uzyskać powiązane informacje zobacz temat "Błąd do obiektu" w Pomocy programu DAO.

Informacje o pobrane przez [CDaoException::GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) funkcja członkowska jest przechowywany w `CDaoErrorInfo` struktury. Sprawdź [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) element członkowski danych z `CDaoException` obiekt, który catch w program obsługi wyjątków lub wywołanie `GetErrorInfo` z `CDaoException` obiekt, który jawnie utworzyć w celu sprawdzenia błędów, które mogą mieć wystąpiły bezpośrednie wywołanie interfejsów DAO. `CDaoErrorInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoErrorInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
