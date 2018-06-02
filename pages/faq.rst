.. title: Frequently Asked Questions (FAQ)
.. slug: faq
.. date: 2018-05-29 19:22:07 UTC+02:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

-  `Benutzer-FAQ`_
-  `Entwickler-FAQ`_

Benutzer-FAQ
------------

Darf ich 7-Zip kommerziell benutzen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ja, 7-Zip ist freie Software. Sie dürfen es auf jedem Computer verwenden. Sie müssen 7-Zip weder registrieren noch dafür bezahlen.

Wie kann ich die Dateiverknüpfungen bei Windows 7 und Vista setzen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sie müssen 7-Zip als Administrator ausführen. Machen Sie einen Rechtsklick auf das Symbol des 7-Zip File Manager und wählen Sie **Als Administrator ausführen**. Dann können Sie die Dateiverknüpfungen und einige andere Optionen auswählen.

Warum können 7z-Archive, die mit einer neuen Version von 7-Zip erstellt wurden, größer sein als Archive, die mit einer alten Version von 7-Zip erstellt wurden?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Neue Versionen von 7-Zip (beginnend mit Version 15.06) nutzen standardmäßig eine andere Sortierreihenfolge für reine 7z-Archive.

Alte Versionen von 7-Zip (vor Version 15.06) sortieren die Dateien „nach Typ“ („nach Erweiterung“).

Neue Versionen von 7-Zip unterstützen zwei Sortierreihenfolgen:

-  sortieren nach Name – standardmäßige Reihenfolge.
-  sortieren nach Typ, falls „\ **qs**\ “ im **Parameter**-Feld bei „Zu Archiv hinzufügen“ ausgewählt ist (oder **-mqs** für die Kommandozeilenversion).

Bei der Kompressionsrate können große Unterschiede für verschiedene Sortierreihenfolgen erzielt werden, falls die Wörterbuchgröße kleiner als die Gesamtgröße der Dateien ist. Falls es ähnliche Dateien in verschiedenen Ordnern gibt, kann „nach Typ“ sortieren manchmal eine bessere Kompressionsrate bringen.

Zu beachten ist, dass „nach Typ“ sortieren einige Nachteile hat. Beispielsweise nutzen NTFS-Laufwerke die Sortierreihenfolge „nach Name“, sodass die Geschwindigkeit von manchen Operationen bei Dateien mit ungewöhnlicher Reihenfolge auf HDD-Geräten fallen kann, falls ein Archiv eine andere Sortierung nutzt (HDDs haben eine geringe Geschwindigkeit für „Such“-Operationen).

Die Kompressionsrate kann mit den folgenden Methoden gesteigert werden:

-  Wörterbuchgröße erhöhen. Das kann helfen, falls „qs“ nicht genutzt wird.
-  „\ **qs**\ “ im **Parameter**-Feld angeben (oder **-mqs**-Switch für die Kommandozeilenversion).

Falls eine ungewöhnliche Dateireihenfolge kein Problem ist und falls eine bessere Kompressionsrate mit einem kleinen Wörterbuch wichtiger ist, sollte der „\ **qs**\ “-Modus genutzt werden.

Warum kann 7-Zip einige ZIP-Archive nicht öffnen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In 99 % der Fälle hat das Archiv einen inkorrekten Header. Andere ZIP-Programme können einige Archive mit falschen Headern öffnen, weil sie Fehler einfach ignorieren.

Falls Sie solch ein Archiv haben, fragen Sie bitte nicht die Entwickler von 7-Zip um Hilfe. Versuchen Sie stattdessen, herauszufinden, mit welchem Programm das Archiv erstellt wurde, und informieren Sie dessen Entwickler, dass ihre Software nicht ZIP-kompatibel ist.

Es gibt auch einige ZIP-Archive, die mit Methoden erstellt wurden, die 7-Zip nicht unterstützt, z. B. WAVPack (WinZip).

Warum kann 7-Zip einige RAR-Archive nicht öffnen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

7-Zip 9.20 unterstützt nur die RAR 2/3/4-Formate und unterstützt keine RAR5-Archive. Die neuesten Versionen von 7-Zip unterstützen allerdings RAR5-Archive.

Warum benutzt 7-Zip temporäre Dateien, wenn Dateien per Drag and Drop aus 7-Zip in den Explorer gezogen werden?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

7-Zip kennt den Zielordner des Drag and Drop nicht, nur der Windows Explorer kennt den Pfad exakt. Windows Explorer benötigt außerdem die Dateien (die Quelldateien des Drag and Drop) als entpackte Dateien auf der Festplatte. 7-Zip dekomprimiert die Dateien also aus dem Archiv in den Temp-Ordner und teilt dem Windows Explorer den Pfad zu den temporären Dateien mit. Der Windows Explorer kopiert anschließend die Dateien in den Zielordner.

Um temporäre Dateien zu vermeiden, können Sie den „Entpacken“-Befehl von 7-Zip oder Drag and Drop von 7-Zip nach 7-Zip benutzen.

Warum fügt die Kommandozeilenversion von 7-Zip keine Dateien ohne Dateinamenerweiterung zu einem Archiv hinzu?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sie benutzen wahrscheinlich \*.\* als Platzhalter. 7-Zip benutzt nicht das Platzhaltersystem des Betriebssystems und behandelt folglich \*.\* als jede Datei, die eine Erweiterung hat. Um alle Dateien zu bearbeiten, müssen Sie deshalb \* benutzen oder ganz auf Platzhalter verzichten.

Warum funktioniert der Schalter „-r“ nicht wie erwartet?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In den meisten Fällen benötigen Sie den „-r“-Schalter gar nicht. 7-Zip kann Unterordner auch ohne „-r“ komprimieren.

Beispiel 1:

::

      7z.exe a c:\a.7z "C:\Program Files"

komprimiert „C:\\Program Files“ vollständig, inklusive aller Unterordner.

Beispiel 2:

::

      7z.exe a -r c:\a.7z "C:\Program Files"

sucht und komprimiert „Program Files“ in allen Unterordnern von C:\\ (z.B. in „C:\\WINDOWS“).

Falls Sie nur Dateien mit einer bestimmten Dateierweiterung komprimieren möchten, können Sie den Schalter „-r“ verwenden:

::

      7z a -r c:\a.zip c:\ordner\*.txt

komprimiert alle \*.txt-Dateien aus dem Ordner c:\\ordner\\ und allen Unterordnern.

Wie kann ich den vollständigen Pfad der Datei im Archiv speichern?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

7-Zip speichert nur relative Dateipfade (ohne Laufwerksbuchstaben). Sie können aber vom aktuellen Ordner in einen Ordner wechseln, der allen zu komprimierenden Dateien gemeinsam ist. Dann können Sie relative Pfade benutzen:

::

      cd /D C:\ordner1\

::

      7z.exe a c:\a.7z datei1.txt ordner2\datei2.txt

Warum kann 7-Zip keine großen Wörterbücher auf 32-bit Windows benutzen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

32-bit Windows weist einer Anwendung höchstens 2 GB virtuellen Speicher zu. Dieser Block von 2 GB kann zusätzlich noch fragmentiert sein (z. B. mit DLL-Dateien), sodass 7-Zip nicht einen großen zusammenhängenden Block virtuellen Speicher bekommen kann. In 64-bit Windows gibt es solche Beschränkungen nicht. Deswegen kann in Windows x64 jedes gewünschte Wörterbuch benutzt werden, falls der nötige physikalische Arbeitsspeicher vorhanden ist.

Wie kann ich 7-Zip im Silent Mode installieren?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Für den EXE-Installer: Mit dem Parameter „/S“ können Sie 7-Zip ohne jegliche Nachfragen („silent“) installieren. Mit dem Parameter „/D=dir“ kann dabei der Zielordner angegeben werden. Bei diesen Optionen wird zwischen Groß- und Kleinschreibung unterschieden.

Für den MSI-Installer: Benutzen Sie die Parameter /q INSTALLDIR="C:\\Program Files\\7-Zip"

Wie kann ich beschädigte 7z-Archive wiederherstellen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Es gibt einige mögliche Fälle, in denen ein Archiv beschädigt ist:

-  Sie können ein Archiv öffnen und die Dateiliste sehen, wenn Sie allerdings „Entpacken“ oder „Überprüfen“ drücken, gibt es einige Fehler: Daten-Fehler oder CRC-Fehler.
-  Wenn Sie ein Archiv öffnen, erhalten Sie die Nachricht: „Kann ‚a.7z‘ nicht als Archiv öffnen“

Es ist möglich, einige Daten wiederherzustellen. Lesen Sie zum Wiederherstellungsprozess:

`How to recover corrupted 7z archive <https://7-zip.org/recover.html>`__ (Link auf die englische 7-Zip-Webseite)

Entwickler-FAQ
--------------

Warum gibt es Linking-Fehler, wenn ich 7-Zip oder LZMA SDK mit Visual C++ 6.0 kompiliere?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Zum Kompilieren der Quelltexte benötigen Sie Visual C++ 6.0 oder neuer. Einige Dateien benötigen auch ein neueres Platform SDK von microsoft.com:

| `http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdk-full.htm <http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdk-full.htm>`__
  oder
| `http://www.microsoft.com/msdownload/platformsdk/sdkupdate/ <http://www.microsoft.com/msdownload/platformsdk/sdkupdate/>`__

Falls Sie MSVC benutzen, geben Sie die SDK-Verzeichnisse zu Beginn der Verzeichnislisten der „Include Dateien“ und der „Bibliothekdateien“ an. Diese finden Sie unter „Extras / Optionen / Verzeichnisse“.

Das neueste Platform SDK ist nicht mit MSVC6 kompatibel. Deswegen müssen Sie Windows Server 2003 PSDK (Februar 2003) mit MSVC6 nutzen.

Darf ich EXE- oder DLL-Dateien von 7-Zip in kommerziellen Anwendungen nutzen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ja, Sie müssen jedoch Folgendes in Ihrer Dokumentation angeben: (1) dass Sie Teile von 7-Zip verwenden, (2) dass 7-Zip unter der GNU LGPL lizensiert ist und (3) müssen Sie einen Verweis zu www.7-zip.org angeben, wo der Quelltext eingesehen werden kann.

Was muss ich tun, damit meine Anwendung auch 7z-Archive unterstützt?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Eine Möglichkeit ist, 7z.dll oder 7za.dll zu benutzen (die Sie bei sf.net herunterladen können). 7za.dll arbeitet mit COM-Interfaces. Es benutzt jedoch nicht gewöhnliche COM-Interfaces zum Erstellen von Objekten. Sie finden ein kleines Beispiel im Ordner „CPP\\7zip\\UI\\Client7z“ im Quelltext. Ein großes Beispiel ist 7-Zip selbst, da 7-Zip auch mit dieser DLL arbeitet. Es gibt auch noch andere Anwendungen, die 7za.dll benutzen, z. B. WinRAR, PowerArchiver und andere.

Eine andere Möglichkeit bietet die Kommandozeilenversion: 7za.exe.

Darf ich den Quelltext von 7-Zip in kommerziellen Anwendungen nutzen?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Da 7-Zip unter der GNU LGPL lizensiert ist, müssen Sie sich an die Regeln dieser Lizenz halten. Kurz gesagt, muss jeder Code, der auf der LGPL basiert, wieder unter die LGPL gestellt werden. Sie können z.B. den Quelltext von 7-Zip ändern oder einen Wrapper für 7-Zip schreiben und diesen in eine DLL kompilieren; der Quelltext dieser DLL (inklusive Ihrer änderungen/Erweiterungen/Wrapper) muss dann jedoch unter die LGPL oder GPL gestellt werden. Jeder andere Code Ihrer Anwendungen kann mit einer beliebigen Lizenz versehen werden. Diese Maßnahme erlaubt es Benutzern und Entwicklern, LGPL-lizensierten Code zu ändern oder die DLL zu rekompilieren. Das ist die Idee hinter freier Software. Für weitere Informationen lesen Sie hier: https://www.gnu.org/. Sie können sich auch über :doc:`LZMA SDK <sdk>` informieren, das unter einer etwas großzügigeren Lizenz steht.

