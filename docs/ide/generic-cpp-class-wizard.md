---
title: Kreator klasy generycznej C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82d706c30c729f490f6bfdec3344d5dab537a689
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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