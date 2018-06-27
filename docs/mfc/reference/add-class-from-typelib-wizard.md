---
title: Biblioteki typów Kreator dodawania klasy z | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.typelib
dev_langs:
- C++
helpviewer_keywords:
- Add Class from TypeLib Wizard [MFC]
- COM interfaces, adding classes
ms.assetid: 96152afd-9374-4649-a6ab-b0fa2a5592a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc26f74de76205041228ce92e29309af1ce8959f
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951679"
---
# <a name="add-class-from-typelib-wizard"></a>Kreator dodawania klasy z biblioteki typów
Ten kreator służy do dodawania klasy MFC z biblioteki typów dostępne. Kreator utworzy klasę dla każdego interfejsu dodawanych z wybranej biblioteki typów.  
  
 **Dodawanie klasy z**  
 Określa lokalizację biblioteki typów, z którego jest tworzony klasy.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Registry**|Biblioteka typów jest zarejestrowana w systemie. Zarejestrowanych bibliotek typów są wymienione w **bibliotek typów dostępne**.|  
|**Plik**|Biblioteki typów nie zawsze jest zarejestrowany w systemie, ale jest zawarty w pliku. Należy podać lokalizację pliku w **lokalizacji**.|  
  
 **Biblioteki typów dostępne**  
 Wyświetla listę bibliotek typów, w obecnie zarejestrowane w systemie. Wybierz bibliotekę typów z tej listy, aby wyświetlić jego interfejsy **interfejsów** listy.  
  
 Zobacz "Wewnątrz rozproszonego modelu COM: typ biblioteki języka integracji i" w bibliotece MSDN, aby uzyskać więcej informacji na temat rejestrowania biblioteki typów.  
  
 **Lokalizacja**  
 Określa lokalizację biblioteki typów. Jeśli klikniesz przycisk **pliku** w obszarze **Dodawanie klasy z**, należy podać lokalizację pliku zawierającego biblioteki typów. Aby przejść do lokalizacji pliku, kliknij przycisk wielokropka.  
  
 **Interfejsy**  
 Wyświetla listę interfejsów w bibliotece typów aktualnie wybrane w **bibliotek typów dostępne** listy.  
  
|Przycisk transferu|Opis|  
|---------------------|-----------------|  
|**>**|Dodaje interfejs aktualnie wybrane w **interfejsów** listy. Nieaktywne, jeśli interfejs nie jest zaznaczone.|  
|**>>**|Dodaje wszystkie interfejsy w bibliotece typów aktualnie wybrane w **bibliotek typów dostępne** listy.|  
|**<**|Usuwa klasy aktualnie wybrane w **wygenerowane klasy** listy. Jeśli klasa nie jest aktualnie wybrane w **wygenerowane klasy** listy.|  
|**<\<**|Usuwa wszystkie klasy w **wygenerowane klasy** listy. Jeśli na wygaszone **wygenerowane klasy** lista jest pusta.|  
  
 **Wygenerowane klasy**  
 Określa nazwę klasy do wygenerowania z interfejsów dodane przy użyciu **>** lub **>>** przycisku. Można kliknąć to pole, aby wybierz klasę, a następnie górę lub w dół klucze do przewijania na liście wyświetlanie nazwy klasy w **klasy** pole i nazwę pliku w **pliku** pole Kreator generuje, kiedy należy Kliknij przycisk **Zakończ**. Jednocześnie można wybrać tylko jedną klasę, w tym polu.  
  
 Klasy można usunąć, wybierając ją na liście i klikając **<**. Nie musisz wybrać klasę w polu klasy generowane, aby usunąć wszystkie klasy; klikając **<<**, należy usunąć wszystkie klasy w **wygenerowane klasy** pole.  
  
 **Class**  
 Określa nazwę klasy wybrany w **wygenerowane klasy** pola, które Kreator dodaje po kliknięciu **Zakończ**. Można edytować nazwy w **klasy** pole.  
  
 **Plik**  
 Ustawia nazwę pliku nagłówka dla nowej klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **wygenerowane klasy**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa MFC z biblioteki typów](../../mfc/reference/adding-an-mfc-class-from-a-type-library.md)   
 [Klienci automatyzacji: korzystanie z bibliotek typów](../../mfc/automation-clients-using-type-libraries.md)

