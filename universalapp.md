# Universal App
Acties te doen in Pluralsight cursus [Introduction to Building Universal Store Apps With C# and XAML]
(http://www.pluralsight.com/courses/building-universal-store-apps-csharp-xaml) 
## Deel 1: demo universal app
* Verplaats Mainpage.Xaml naar shared project
* Voeg usercontrol toe aan Windows Phone project
* Copy usercontrol naar Windows project (drag+drop)
* Pas in beide usercontrols iets aan zodat ze niet meer identiek zijn
* Voeg usercontrol toe in mainpage.xaml (vergeet xmlns referentie niet)
* Test applicatie in beide versie en merk het verschil op

### Opmerking
Beide applicaties kunnen tegelijkertijd via F5 gestart worden:
* Rechterklik op Solution
* Ga naar Startup Project (onder Common Properties) 
* Kies "Multiple startup projects"
* Zet als action "start" bij beide projecten.

###  Deel 2: conditional compilation

* Voeg appbar boven en onderaan mainpage toe. Bboven en onder grid in xaml voeg je volgende code toe:
'''
<Page.TopAppBar>
        <AppBar>
            <StackPanel Height="300" Orientation="Horizontal" HorizontalAlignment="Stretch" Background="Pink"></StackPanel>
        </AppBar>
</Page.TopAppBar>
'''
en
'''
<Page.BottomAppBar>
        <CommandBar Background="Green">
            <AppBarButton Icon="Like" Label="Like"/>
            <AppBarButton Icon="Clock" Label="Navigate"></AppBarButton>
        </CommandBar>
    </Page.BottomAppBar>
'''