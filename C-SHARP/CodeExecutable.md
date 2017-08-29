# Code exécutable :

### [Tuto : MVVM First Application](https://www.tutorialspoint.com/mvvm/mvvm_first_application.htm)

### Définition : Forme directement utilisable d'un programme informatique, après compilation

On parle de code source et de code exécutable dans le cas des programmes qui doivent être compilés pour être exécutés (soit la majorité des programmes).Le code exécutable, c'est la forme qu'a le programme après sa compilation. Les instructions écrites à l'origine en langage de programmation sont traduites en séquences d'opérations adaptées au microprocesseur utilisé, et le programme peut s'exécuter sans faire appel à un autre programme mais directement depuis le système dexploitation.

### Step by Step :

#### Création des différentes parties du projet (/solution sous Visual Studio) :

  1. Model : Le Model dans l'application est rempli par des reqûetes de données via APIS et connections avec une BDD, ainsi que la logique;
  
  2. ViewModel : La VueModel agit comme un intermédiaire entre la Vue et le Model, c'est lui qui va gérer la logique dans la Vue. EN général, la VM interagi avec le Model via les Methodes dans les Class du Modèle. La VM récupère donc des données du Model dans un format que la Vue peut traiter. Il est possible que le Model, en récupérant des données reformate ces-dernières pour qu'elles soient gérer plus facilement dans la Vue.
  Depuis la Vue , l'utilisateur peut intéragir avec des champs ou des boutons qui vont, en cliquant dessus ou en tapant un texte, modifier un état. C'est la VM qui va s'occuper de ces changements grâce au two-way Binding depuis la Vue, en amont il faudra alors définir des propriétes avec l'événement PropertyChanged. VM a aussi besoin d'implémenter l'interface INotifyPropertyChanged et de remonter l'événement PropertyChanged quand il est changé. (Pour les collections : the view-friendly System.Collections.ObjectModel.ObservableCollection<T> is provided,implement the INotifyCollectionChanged interface on collections.);
  
  3. View : La Vue est la couche qui va gérer l'apparence. C'est ce que l'utilisateur va voir sur son écran. Idéalement, la Vue est définie seulement en XAML, avec peu de code contenant de la logique.
