---
title: Kreator dostawcy interfejsu OLE DB ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.provider.overview
dev_langs: C++
helpviewer_keywords:
- ATL OLE DB Provider Wizard
- ATL projects, adding ATL OLE DB providers
ms.assetid: cf91ba78-01d1-4d12-b673-e95d96bfbebe
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 170f10d06112969d9147c37b20572f0888140d0a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-ole-db-provider-wizard"></a>Kreator dostawcy interfejsu OLE DB ATL
Ten kreator tworzy klasy, które tworzą dostawcy OLE DB.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual Studio 2008 skryptu rejestracji utworzone przez tego kreatora zarejestruje jego składniki modelu COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **składnik rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
 W poniższej tabeli opisano opcje OLE DB Provider Kreator ATL:  
  
 **Krótka nazwa**  
 Wpisz krótką nazwę dostawcy, który ma zostać utworzony. Pozostałe pola edycji kreatora zostaną wypełnione automatycznie na podstawie w tym miejscu wpisz. Jeśli chcesz, możesz edytować pozostałe pola nazw.  
  
 **Klasa coclass**  
 Nazwa klasy coclass. Nazwa identyfikatora ProgID zostanie zmieniona na odpowiada podanej nazwie.  
  
 **Atrybut**  
 Ta opcja określa, czy Kreator utworzy za pomocą atrybutów lub deklaracji szablonu klasy dostawcy. Po wybraniu tej opcji, kreator używa atrybutów zamiast deklaracji szablonu (to jest domyślną opcją w przypadku utworzenia projekcie z atrybutami). Gdy ta opcja zostanie wyłączona, kreator używa deklaracji szablonu zamiast atrybutów (to jest domyślną opcją w przypadku bezatrybutowego projekt został utworzony).  
  
 Wybranie tej opcji podczas tworzenia projektu bezatrybutowego Kreator wyświetli ostrzeżenie, że projekt zostanie przekonwertowany na projekcie z atrybutami i zapyta, czy kontynuować, lub nie.  
  
 **Identyfikator programu**  
 Identyfikator ProgID lub identyfikator programowy, to ciąg tekstowy, który aplikacja może używać zamiast identyfikatora GUID. Nazwa identyfikatora ProgID ma formę *NazwaProjektu.nazwaklasycoclass*.  
  
 **Wersja**  
 Numer wersji dostawcy. Domyślnym ustawieniem jest 1.  
  
 **Klasa źródła danych**  
 Nazwa klasy źródła danych w postaci C*nazwa_skrócona*źródła.  
  
 **Źródło danych w pliku .h**  
 Plik nagłówka klasy źródła danych. Możesz zmienić nazwę tego pliku lub wybierz istniejący plik nagłówka.  
  
 **Klasa sesji**  
 Nazwa klasy sesji formularza C*nazwa_skrócona*sesji.  
  
 **Plik .h sesji**  
 Plik nagłówka klasy sesji. Możesz zmienić nazwę tego pliku lub wybierz istniejący plik nagłówka.  
  
 **Polecenie — klasa**  
 Nazwa klasy poleceń formularza C*nazwa_skrócona*polecenia.  
  
 **Polecenie .h pliku**  
 Plik nagłówka klasy poleceń. Ta nazwa nie może być edytowany i jest zależna od nazwy pliku nagłówka zestawu wierszy.  
  
 **Klasy zestawu wierszy**  
 Nazwa klasy zestawu wierszy formularza C*nazwa_skrócona*zestawu wierszy.  
  
 **Zestaw wierszy w pliku .h**  
 Plik nagłówka klasy zestawu wierszy. Możesz zmienić nazwę tego pliku lub wybierz istniejący plik nagłówka.  
  
 **Plik .cpp zestawu wierszy**  
 Plik implementacji dostawcy. Możesz zmienić nazwę tego pliku lub wybierz istniejący plik implementacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca ATL OLE DB](../../atl/reference/adding-an-atl-ole-db-provider.md)

