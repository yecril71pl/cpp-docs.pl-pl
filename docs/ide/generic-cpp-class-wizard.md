---
title: Kreator klasy generycznej C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e86a4047ef025f49dd01eda90f324623a90752
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33328308"
---
# <a name="generic-c-class-wizard"></a>Kreator klasy generycznej C++
Dodaje klasy ogólnej C++ do projektu. Klasa nie dziedziczy z ATL ani MFC.  
  
 **Nazwa klasy**  
 Ustawia nazwę nowej klasy.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Aby zapisać plik nagłówka wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy, kliknij przycisk oznaczony wielokropkiem (**...** ). Jeśli określisz istniejący plik, po kliknięciu **Zakończ**, Kreator wyświetli monit o określenie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Aby dołączyć deklaracji, kliknij przycisk **tak**; aby powrócić do kreatora i podaj inną nazwę pliku, kliknij przycisk **nr**.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **Nazwa klasy**. Aby zapisać plik implementacji w wybranej lokalizacji lub do dołączenia do istniejącego pliku definicji klasy, kliknij przycisk oznaczony wielokropkiem (**...** ). Jeśli określisz istniejący plik, po kliknięciu **Zakończ**, Kreator wyświetli monit o określenie, czy w definicji klasy powinna zostać dołączona do zawartości pliku. Aby dołączyć definicji, kliknij przycisk **tak**; aby powrócić do kreatora i podaj inną nazwę pliku, kliknij przycisk **nr**.  
  
 **Klasa podstawowa**  
 Ustawia klasę podstawową dla nowej klasy.  
  
 **Dostęp**  
 Ustawia dostęp do elementów członkowskich klasy podstawowej dla nowej klasy. Modyfikatory dostępu są słowa kluczowe, które określają poziom dostępu do funkcji Członkowskich klasy innych klas. Aby uzyskać więcej informacji na temat określania dostępu, zobacz [kontroli dostępu elementu członkowskiego](../cpp/member-access-control-cpp.md). Domyślny poziom dostępu do klasy jest ustawiony na `public`.  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **Domyślna** (nie modyfikator dostępu jest generowany).  
  
 **Destruktor wirtualny**  
 Określa, czy wirtualny destruktor klasy. Użyj destruktor wirtualny pomaga, upewnij się, że poprawne destruktora jest wywoływane w przypadku wystąpienia klas pochodnych są usuwane.  
  
 **Wbudowany**  
 Generuje zarówno konstruktora klasy, jak i definicja klasy jako funkcje wbudowane w pliku nagłówka.  
  
 **Zarządzane**  
 Po wybraniu dodaje plik zarządzanej klasy i nagłówek. Po wyczyszczeniu dodaje natywny plik klasy i nagłówek.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie rodzajowej klasy C++](../ide/adding-a-generic-cpp-class.md)