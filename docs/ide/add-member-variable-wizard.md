---
title: "Kreator dodawania zmiennej członkowskiej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.variable.overview
dev_langs: C++
helpviewer_keywords: Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 28be63dffff7d89b4967363670263f78b98d398a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="add-member-variable-wizard"></a>Kreator dodawania zmiennej członkowskiej
Ten kreator dodaje deklaracji zmiennej członka do pliku nagłówka i, w zależności od opcji, go dodać kod do pliku .cpp. Po dodaniu zmiennej członkowskiej, za pomocą kreatora można edytować kodu w środowisku programistycznym.  
  
 **Dostęp**  
 Ustawia dostęp do zmiennej elementu członkowskiego. Modyfikatory dostępu są słów kluczowych, które Określ dostęp innych klas, że zmienna członka. Zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) Aby uzyskać więcej informacji na temat określania dostępu. Ustawiono poziom dostępu do zmiennych Członkowskich **publicznego** domyślnie.  
  
-   [publiczny](../cpp/public-cpp.md)  
  
-   [chronione](../cpp/protected-cpp.md)  
  
-   [prywatne](../cpp/private-cpp.md)  
  
 **Typ zmiennej**  
 Ustawia typ zwrotny dla zmiennej członkowskiej, który dodajesz.  
  
-   W przypadku dodawania zmiennej członkowskiej, która nie jest kontrolka okna dialogowego, wybierz z listy dostępnych typów.  
  
     Aby uzyskać informacje o typach, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).  
  
    |||  
    |-|-|  
    |`char`|**krótki**|  
    |**podwójne**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**długa**||  
  
-   W przypadku dodawania zmiennej członkowskiej dla kontrolka okna dialogowego, to pole jest wypełniane z typem obiektu zwróconego dla formantów i wartość. W przypadku wybrania **kontroli**, następnie **typ zmiennej** Określa klasę podstawową formantu, należy wybrać w **Identyfikatora formantu** pole. Jeśli kontrolka okna dialogowego może zawierać wartości, a w przypadku wybrania **wartość**, następnie **typ zmiennej** Określa typ odpowiednią wartość, która może zawierać formant. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.  
  
     Ta wartość jest zależna od zaznaczenia w **Identyfikatora formantu** i nie można zmienić.  
  
 **Nazwa zmiennej**  
 Ustawia nazwę zmiennej członkowskiej, który dodajesz. Zmienne Członkowskie zaczynają zwykle ciąg identyfikujący "m_", który jest dostarczany domyślnie.  
  
 **Zmienna sterująca**  
 Wskazuje, że zmiennej członkowskiej zarządza formantu w oknie dialogowym z [danych wymiana i Walidacja danych](../mfc/dialog-data-exchange-and-validation.md) obsługuje. Zobacz [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) Aby uzyskać więcej informacji. Ta opcja jest dostępna tylko dla zmiennych Członkowskich dodany do klasy pochodzące od [cdialog —](../mfc/reference/cdialog-class.md). Zaznacz to pole, aby aktywować **Identyfikatora formantu** i **kontroli typem** opcje.  
  
 **Identyfikator formantu**  
 Ustawia identyfikator dla zmiennej formantu, który dodajesz. Wybierz z listy identyfikator dla typu formantu dodawania zmiennej członkowskiej. Lista jest aktywny tylko wtedy, gdy **zmienna sterująca** zaznaczone pole i jest ograniczone do identyfikatorów formantów już dodany do okna dialogowego. Na przykład w przypadku standardowego **OK** jest identyfikator formantu przycisku **IDOK**.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Formant**|Ta opcja jest domyślnie dla typu formantu. (Jak można wykonać za pomocą pola listy, pola kombi lub pola edycji) zarządza kontroli siebie i nie stanie lub zawartość formantu.|  
|**Wartość**|Ta opcja jest dostępna tylko dla typów kontroli, które mogą zawierać wartości (takie jak pole edycji) lub odzwierciedlają stan (na przykład pole wyboru) i dla których może zarządzać zakresu, zawartości lub stanu. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.|  
  
 **Kategoria**  
 Określa, czy zmienna jest oparta na typu lub wartość formantu.  
  
 **Typ formantu**  
 Ustawia typ kontroli dodawany. To pole nie jest dostępna. Na przykład przycisk ma typ formantu **przycisk**, a pole kombi ma typ formantu **COMBOBOX**. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.  
  
 **Maksymalna liczba znaków**  
 Dostępne tylko wtedy, gdy **typ zmiennej** ustawiono [cstring —](../atl-mfc-shared/reference/cstringt-class.md). Wskazuje maksymalną liczbę znaków, które mogą zawierać formantu.  
  
 **Wartość minimalna**  
 Dostępne tylko wtedy, gdy typ zmiennej **BOOL**, `int`, **UINT**, **długi**, `DWORD`, **float**, **podwójne**, **BAJTÓW**, **krótki**, [COLECurrency](../mfc/reference/colecurrency-class.md) lub [ctime —](../atl-mfc-shared/reference/ctime-class.md). Wskazuje wartość najniższy dopuszczalny zakres skali lub daty.  
  
 **Wartość maksymalna**  
 Dostępne tylko wtedy, gdy typ zmiennej **BOOL**, `int`, **UINT**, **długi**, `DWORD`, **float**, **podwójne**, **BAJTÓW**, **krótki**, `COLECurrency` lub `CTime`. Wskazuje wartość najwyższy dopuszczalny zakres skali lub daty.  
  
 **w pliku .h**  
 Dla formantów ActiveX, których zmiennych Członkowskich wymagają klasy otoki. Ustawia nazwę pliku nagłówka do dodania deklaracji klasy.  
  
 **plik .cpp**  
 Dla formantów ActiveX, których zmiennych Członkowskich wymagają klasy otoki. Ustawia nazwę pliku implementacji, aby dodać definicji klasy.  
  
 **Komentarz**  
 Zawiera komentarz w pliku nagłówka zmiennej członka.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)