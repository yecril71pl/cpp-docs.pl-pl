---
title: Formant ActiveX, Kreator dodawania klasy z | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.axcontrol
dev_langs:
- C++
helpviewer_keywords:
- ActiveX Control Wizard
- Add Class from ActiveX Control Wizard [C++]
ms.assetid: 668d801c-5fb6-4176-9191-5c38995a4713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ab96943e47287c9b54753c8d3a1edb868804274
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="add-class-from-activex-control-wizard"></a>Kreator dodawania klasy z kontrolki ActiveX
Ten kreator służy do dodawania klasy MFC z formantu ActiveX dostępne. Kreator utworzy klasę dla każdego interfejsu dodawanych z wybranej kontrolki ActiveX.  
  
 **Dodawanie klasy z**  
 Określa lokalizację biblioteki typów, z którego jest tworzony klasy.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Registry**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowanych bibliotek typów są wymienione w **kontrolki ActiveX dostępne**.|  
|**Plik**|Biblioteki typów nie zawsze jest zarejestrowany w systemie, ale jest zawarty w pliku. Należy podać lokalizację pliku w **lokalizacji**.|  
  
 **Dostępne formantów ActiveX**  
 Określa formantów ActiveX w danym momencie zarejestrowany w systemie. Wybierz kontrolkę ActiveX z tej listy, aby wyświetlić jego interfejsy w **interfejsów** listy. Zobacz [kontrolki ActiveX MFC: Dystrybucja formantów ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) Aby uzyskać więcej informacji na temat rejestrowanie formantów ActiveX.  
  
 Jeśli klikniesz przycisk **pliku** w obszarze **Dodawanie klasy z**, to pole jest niedostępna w przypadku zmiany.  
  
 **Lokalizacja**  
 Określa lokalizację formantu ActiveX. Jeśli klikniesz przycisk **pliku** w obszarze **Dodawanie klasy z**, należy podać lokalizację pliku zawierającego biblioteki typów. Aby przejść do lokalizacji pliku, kliknij przycisk wielokropka.  
  
 Jeśli klikniesz przycisk **rejestru** w obszarze **Dodawanie klasy z**, to pole jest niedostępna w przypadku zmiany.  
  
 **Interfejsy**  
 Określa interfejsy w aktualnie zaznaczonego w formancie ActiveX **kontrolki ActiveX dostępne** lub w bibliotece typów w określonym w pliku **lokalizacji**.  
  
|Przycisk transferu|Opis|  
|---------------------|-----------------|  
|**>**|Dodaje interfejs aktualnie wybrane w **interfejsów** listy. Parametr jest niedostępne, jeśli interfejs nie jest zaznaczone.|  
|**>>**|Dodaje wszystkie interfejsy w aktualnie zaznaczonego w formancie ActiveX **kontrolki ActiveX dostępne** lub w bibliotece typów w określonym w pliku **lokalizacji**.|  
|**<**|Usuwa klasy aktualnie wybrane w **wygenerowane klasy** listy. Niedostępne, jeśli klasa nie jest aktualnie zaznaczone w **wygenerowane klasy** listy.|  
|**<\<**|Usuwa wszystkie klasy w **wygenerowane klasy** listy. Niedostępne w przypadku **wygenerowane klasy** lista jest pusta.|  
  
 **Wygenerowane klasy**  
 Określa nazwę klasy do wygenerowania z interfejsów dodane przy użyciu **>** lub **>>** przycisku. Można kliknąć to pole, aby wybierz klasę, a następnie górę lub w dół klucze do przewijania na liście wyświetlanie nazwy klasy w `Class` pole i nazwę pliku w **pliku .h** pola, które generuje kreatora po kliknięciu  **Zakończ**. Jednocześnie można wybrać tylko jedną klasę, w tym polu.  
  
 Klasy można usunąć, wybierając ją na liście i klikając **<**. Nie musisz wybrać klasę w **wygenerowane klasy** pole, aby usunąć wszystkie klasy, a przez kliknięcie przycisku **<<**, należy usunąć wszystkie klasy w **wygenerowane klasy** pole.  
  
 `Class`  
 Określa nazwę klasy wybrany w **wygenerowane klasy** pola, które Kreator dodaje po kliknięciu **Zakończ**. Można edytować nazwy w `Class` pole.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie klasy z formantu ActiveX](../ide/adding-a-class-from-an-activex-control-visual-cpp.md)   
 [Klienci automatyzacji: korzystanie z bibliotek typów](../mfc/automation-clients-using-type-libraries.md)