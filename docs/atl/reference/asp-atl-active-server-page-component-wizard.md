---
title: ASP, Kreator składników stron Active Server ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.asp
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 210ef0d41cd0653718908b10ad64cd6004886c64
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077754"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Kreator składników stron Active Server ATL

Ta strona ATL Active Server strona kreatora składników umożliwia określić opcjonalne ustawienia do obsługi informacji i stanu związane z składnik ASP.

- **Opcjonalny metody**

   Dodaje metody opcjonalne ASP **OnStartPage** i **OnEndPage**, do obiektu. Należy wybrać tę opcję można ustawić wszystkie wewnętrzne obiekty Active Server Pages. Domyślnie jest zaznaczona.

- **Metoda OnStartPage/OnEndPage**

   [Metoda OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) jest wywoływana po raz pierwszy skrypt próbuje uzyskać dostęp do obiektu. **OnEndPage** jest wywoływana po zakończeniu operacji obiektu przetwarzania skryptu.

- **Obiekt wewnętrzny**

   Musisz wybrać **OnStartPage/OnEndPage** opcję, aby ustawić wszystkie obiekty wewnętrzne środowiska ASP.

|Opcja|Opis|
|------------|-----------------|
|**Żądanie**|Zapewnia dostęp do strony ASP wewnętrzne **żądania** obiektu. Obiekt żądania jest używany do przekazania żądania HTTP.|
|**Odpowiedź**|Zapewnia dostęp do strony ASP wewnętrzne **odpowiedzi** obiektu. W odpowiedzi na żądanie w obiekt odpowiedzi wysyła informacje do przeglądarki do wyświetlania użytkownikowi.|
|**Sesja**|Zapewnia dostęp do strony ASP wewnętrzne **sesji** obiektu. **Sesji** obiekt przechowuje informacje o bieżącej sesji użytkownika, w tym przechowywania i pobierania informacji o stanie.|
|**Aplikacja**|Zapewnia dostęp do strony ASP wewnętrzne **aplikacji** obiektu. **Aplikacji** zarządza obiekt stanu, który jest współużytkowany przez wiele obiektów ASP.|
|**Serwer**|Zapewnia dostęp do strony ASP wewnętrzne **serwera** obiektu. **Serwera** obiektu pozwala na tworzenie innych obiektów ASP.|

## <a name="see-also"></a>Zobacz też

[Kreator składników stron Active Server Page ATL](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Składnika strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

