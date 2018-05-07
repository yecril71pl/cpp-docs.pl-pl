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
ms.openlocfilehash: 349d06d7fecb82af64fbf2d3b2ebe54689b3b292
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adding-an-mfc-class-from-a-type-library"></a>Dodawanie klasy MFC z biblioteki typów
Ten kreator umożliwia tworzenie klasy MFC z interfejsu w bibliotece typów dostępne. Można dodać klasy MFC do [aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md), [biblioteki MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md), lub [kontrolki MFC ActiveX](../../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Nie ma konieczności tworzenia projektu MFC automatyzacji umożliwia dodawanie klasy z biblioteki typów.  
  
 Biblioteki typów zawiera opis binarne interfejsów udostępnianych przez składnik definiujący metody wraz z ich parametrów i zwracanych typów. Biblioteki typu musi być zarejestrowany pojawią się w **bibliotek typów dostępne** liście dodawania klasy z Typelib kreatora. Zobacz "Wewnątrz rozproszonego modelu COM: typ biblioteki języka integracji i" w bibliotece MSDN, aby uzyskać więcej informacji.  
  
### <a name="to-add-an-mfc-class-from-a-type-library"></a>Dodawanie klasy MFC z biblioteki typów  
  
1.  W jednym **Eksploratora rozwiązań** lub [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę projektu, do której chcesz dodać klasę.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  W [Dodaj klasę](../../ide/add-class-dialog-box.md) kliknij okno dialogowe, w okienku szablonów **klasa MFC z biblioteki typów**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [dodawania klasy z Typelib Kreatora ](../../mfc/reference/add-class-from-typelib-wizard.md).  
  
 W kreatorze można dodać więcej niż jedną klasę w bibliotece typów. Podobnie możesz dodawać klasy z więcej niż jedną bibliotekę typów w jednej sesji kreatora.  
  
 Kreator utworzy klasę MFC pochodną [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md), dla każdego interfejsu należy dodać z wybranej biblioteki typów. `COleDispatchDriver` Implementuje automatyzacji OLE po stronie klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Klienci automatyzacji](../../mfc/automation-clients.md)   
 [Klienci automatyzacji: korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)

