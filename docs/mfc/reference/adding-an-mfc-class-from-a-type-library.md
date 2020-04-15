---
title: Dodawanie klasy MFC z biblioteki typów
ms.date: 11/04/2016
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
ms.openlocfilehash: bf9c763a215a4880d5b0ad206f6a347341fea9eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371719"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Dodawanie klasy MFC z biblioteki typów

Ten kreator służy do tworzenia klasy MFC z interfejsu w dostępnej bibliotece typów. Klasy MFC można dodać do [aplikacji MFC,](../../mfc/reference/creating-an-mfc-application.md) [biblioteki DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md)lub [kontrolki MFC ActiveX.](../../mfc/reference/creating-an-mfc-activex-control.md)

> [!NOTE]
> Nie trzeba tworzyć projektu MFC z automatyzacji włączone, aby dodać klasę z biblioteki typów.

Biblioteka typów zawiera binarny opis interfejsów udostępniane przez składnik, definiowanie metod wraz z ich parametrów i zwracanych typów. Biblioteka typów musi być zarejestrowana, aby była wyświetlana na liście **Dostępne biblioteki typów** w Kreatorze dodawania klasy z Aplikacji Typelib. Zobacz "Wewnątrz rozproszonej COM: Biblioteki typu i integracji języka" w bibliotece MSDN, aby uzyskać więcej informacji.

### <a name="to-add-an-mfc-class-from-a-type-library"></a>Aby dodać klasę MFC z biblioteki typów

1. W **Eksploratorze rozwiązań** lub [widoku klasy](/visualstudio/ide/viewing-the-structure-of-code)kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać klasę.

1. W menu skrótów kliknij polecenie **Dodaj**, a następnie kliknij polecenie **Dodaj klasę**.

1. W oknie dialogowym [Dodawanie klasy](../../ide/add-class-dialog-box.md) w okienku Szablony kliknij pozycję **Klasa MFC z typelib**, a następnie kliknij przycisk **Otwórz,** aby wyświetlić [Kreatora dodawania klasy z narzędzia Typelib](../../mfc/reference/add-class-from-typelib-wizard.md).

W kreatorze można dodać więcej niż jedną klasę w bibliotece typów. Podobnie można dodać klasy z więcej niż jednej biblioteki typów w jednej sesji kreatora.

Kreator tworzy klasę MFC, pochodzące z [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), dla każdego interfejsu dodawane z biblioteki typów wybranego. `COleDispatchDriver`implementuje po stronie klienta automatyzacji OLE.

## <a name="see-also"></a>Zobacz też

[Klienci automatyzacji](../../mfc/automation-clients.md)<br/>
[Klienci automatyzacji: korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)
