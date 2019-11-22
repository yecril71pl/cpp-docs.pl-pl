---
title: CDaoErrorInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 8d731c8e8bea1adc850ab3c00c7688b9f8c9b819
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304229"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo — Struktura

Struktura `CDaoErrorInfo` zawiera informacje o obiekcie błędu zdefiniowanym dla obiektów dostępu do danych (DAO). Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

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
Liczbowy kod błędu DAO. Zapoznaj się z tematem "błędy dostępu do danych z pułapkami" w pomocy programu DAO.

*m_strSource*<br/>
Nazwa obiektu lub aplikacji, która pierwotnie wygenerowała błąd. Właściwość Source określa wyrażenie ciągu reprezentujące obiekt, który pierwotnie wygenerował błąd; wyrażenie jest zazwyczaj nazwą klasy obiektu. Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość Source" w pomocy DAO.

*m_strDescription*<br/>
Opisowy ciąg skojarzony z błędem. Aby uzyskać szczegółowe informacje, zobacz temat "opis właściwości" w pomocy DAO.

*m_strHelpFile*<br/>
W pełni kwalifikowana ścieżka do pliku pomocy systemu Microsoft Windows. Aby uzyskać szczegółowe informacje, zobacz temat "atrybut HelpContext, HelpFile Properties" w pomocy DAO.

*m_lHelpContext*<br/>
Identyfikator kontekstu tematu w pliku pomocy systemu Microsoft Windows. Aby uzyskać szczegółowe informacje, zobacz temat "atrybut HelpContext, HelpFile Properties" w pomocy DAO.

## <a name="remarks"></a>Uwagi

MFC nie hermetyzuje obiektów błędów DAO w klasie. Zamiast tego Klasa [CDaoException](../../mfc/reference/cdaoexception-class.md) dostarcza interfejs do uzyskiwania dostępu do kolekcji Errors zawartej w obiekcie DAO `DBEngine`, obiekt, który również zawiera wszystkie obszary robocze. Gdy operacja MFC DAO zgłasza obiekt `CDaoException`, który przechwytuje, MFC wypełnia strukturę `CDaoErrorInfo` i zapisuje ją w elemencie członkowskim [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) obiektu wyjątku. (W przypadku wybrania bezpośredniego wywoływania obiektów DAO należy wywołać funkcję elementu członkowskiego [GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) obiektu Exception samodzielnie, aby wypełnić `m_pErrorInfo`).

Aby uzyskać więcej informacji na temat obsługi błędów DAO, zobacz [wyjątki w artykule: wyjątki bazy danych](../../mfc/exceptions-database-exceptions.md). Aby uzyskać powiązane informacje, zobacz temat "błąd obiektu" w pomocy DAO.

Informacje pobierane przez funkcję członkowską [CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) są przechowywane w strukturze `CDaoErrorInfo`. Sprawdź element członkowski danych [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) z obiektu `CDaoException`, który znajduje się w obsłudze wyjątków, lub wywołaj `GetErrorInfo` z obiektu `CDaoException` utworzonego jawnie w celu sprawdzenia błędów, które mogły wystąpić podczas bezpośredniego wywołania interfejsów DAO. `CDaoErrorInfo` również definiuje funkcję członkowską `Dump` w kompilacjach debugowania. Aby zrzucić zawartość obiektu `CDaoErrorInfo`, można użyć `Dump`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoException](../../mfc/reference/cdaoexception-class.md)
