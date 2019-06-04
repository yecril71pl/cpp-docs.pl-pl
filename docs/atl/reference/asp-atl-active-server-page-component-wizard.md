---
title: ASP, Kreator składników stron Active Server ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: b88dffe2874d29918315af65c6ea093c24695f97
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503412"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Kreator składników stron Active Server ATL

Ta strona ATL Active Server strona kreatora składników umożliwia określić opcjonalne ustawienia do obsługi informacji i stanu związane z składnik ASP.

- **Opcjonalny metody**

   Dodaje metody opcjonalne ASP **OnStartPage** i **OnEndPage**, do obiektu. Należy wybrać tę opcję można ustawić wszystkie wewnętrzne obiekty Active Server Pages. Domyślnie jest zaznaczona.

- **OnStartPage/OnEndPage**

   [Metoda OnStartPage](/previous-versions//ms691624\(v=vs.85\)) jest wywoływana po raz pierwszy skrypt próbuje uzyskać dostęp do obiektu. **OnEndPage** jest wywoływana po zakończeniu operacji obiektu przetwarzania skryptu.

- **Obiekt wewnętrzny**

   Musisz wybrać **OnStartPage/OnEndPage** opcję, aby ustawić wszystkie obiekty wewnętrzne środowiska ASP.

|Opcja|Opis|
|------------|-----------------|
|**Żądanie**|Zapewnia dostęp do strony ASP wewnętrzne **żądania** obiektu. Obiekt żądania jest używany do przekazania żądania HTTP.|
|**Odpowiedź**|Zapewnia dostęp do strony ASP wewnętrzne **odpowiedzi** obiektu. W odpowiedzi na żądanie w obiekt odpowiedzi wysyła informacje do przeglądarki do wyświetlania użytkownikowi.|
|**Sesja**|Zapewnia dostęp do strony ASP wewnętrzne **sesji** obiektu. **Sesji** obiekt przechowuje informacje o bieżącej sesji użytkownika, w tym przechowywania i pobierania informacji o stanie.|
|**Aplikacja**|Zapewnia dostęp do strony ASP wewnętrzne **aplikacji** obiektu. **Aplikacji** zarządza obiekt stanu, który jest współużytkowany przez wiele obiektów ASP.|
|**Serwer**|Zapewnia dostęp do strony ASP wewnętrzne **serwera** obiektu. **Serwera** obiektu pozwala na tworzenie innych obiektów ASP.|

## <a name="see-also"></a>Zobacz także

[Kreator składników stron Active Server Page ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Składnika strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
