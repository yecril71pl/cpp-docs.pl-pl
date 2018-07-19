---
title: Dodawanie klasy MFC z biblioteki typu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- classes [MFC], adding MFC
- MFC, adding classes from type libraries
- type libraries, adding MFC classes from
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 662754ae4f0f95160f18682f35eb2f7951e7e344
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026555"
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Dodawanie klasy MFC z biblioteki typów
Ten kreator umożliwia tworzenie klasy MFC z biblioteki dostępnych typów interfejsu. Można dodać klasy MFC do [aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md), [biblioteki MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md), lub [kontrolki MFC ActiveX](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Nie trzeba tworzyć projektu MFC przy użyciu usługi Automation, możliwość dodawania klasy z biblioteki typów.  
  
 Biblioteka typów zawiera opis binarne interfejsów udostępnianego przez składnik, definiowania metod wraz z ich parametrów i zwracanych typów. Twoja Biblioteka typów musi być zarejestrowana do będzie wyświetlana na **bibliotek typów dostępnych** liście dodawania klasy z Typelib kreatora. Zobacz "Wewnątrz rozproszonego modelu COM: typ biblioteki i język Integration" w bibliotece MSDN, aby uzyskać więcej informacji.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>Dodawanie klasy MFC z biblioteki typów  
  
1.  W obu **Eksploratora rozwiązań** lub [Widok klas](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać klasę.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  W [Dodaj klasę](../../ide/add-class-dialog-box.md) kliknij w okienku szablonów, w oknie dialogowym **klasy MFC z biblioteki typów**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [dodawania klasy z Typelib Kreatora ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 W kreatorze możesz dodać więcej niż jednej klasy w bibliotece typów. Podobnie można dodać klasy z więcej niż jednej biblioteki typów w jednej sesji kreatora.  
  
 Kreator utworzy klasę MFC pochodną [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), dla każdego interfejsu, możesz dodać z wybranej biblioteki typów. `COleDispatchDriver` implementuje po stronie klienta automatyzację OLE.  
  
## <a name="see-also"></a>Zobacz też  
 [Klienci automatyzacji](../../mfc/automation-clients.md)   
 [Klienci automatyzacji: korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)

