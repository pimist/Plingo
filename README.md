# Plingo

/**
 * Welcome to Pebble.js!
 *
 * This is where you write your app.
 */
var UI = require('ui');
var Vector2 = require('vector2');
var natlan = '';
var dirlan = '';
var translan = '';
//"pick a language" in other languages
var pickLan = ["Wählen Sie Sprache , um Übersetzen", "Pick Language to Translate", "Elija idioma a traducir", "Choisissez langue à traduire", "Escolha idioma para traduzir"];
//"Pick Directory" in other languages
var direcLan = ["Pick- Verzeichnis", "Pick Directory", "Escoja Directorio", "Choisissez Répertoire", "Escolha Diretório"];
//"Phrases and Questions" in other languages
var phraLan = ["Phasen & Fragen", "Phrases and Questions", "Fases & Preguntas", "Phases & Questions", "Fases e Perguntas"];
//Languages in other languages
var engLan = ["German", "English", "Spanish", "French", "Portoguese"];
var frnLan = ["Allemand", "Anglais", "Espagnol", "Français", "Portugais"];
var spnLan = ["Alemán", "Inglés", "Español", "Francés", "Portugués"];
var gerLan = ["Deutsche", "Englisch", "Spanisch", "Französisch", "Portugiesisch"];
var porLan = ["Alemão", "Inglês", "Espanhol", "Francês", "Português"];
var lLan = [gerLan, engLan, spnLan, frnLan, porLan];
//Directory in other languages
var engDir = ["General", "Friendly", "Directions", "Shopping", "Help"];
var frnDir = ["Général", "Amicale", "Directions", "Courses", "Aidez-moi"];
var spnDir = ["General", "Amistoso", "Direcciones", "Compras", "Ayuda"];
var gerDir = ["General", "Freundlich", "Wegbeschreibung", "Einkaufen", "Hilfe"];
var porDir = ["Geral", "Amigável ", "Instruções", "Compras", "Socorro"];
var dLan = [gerDir, engDir, spnDir, frnDir, porDir];
//General phrases
var engGen = ["1.Hello!", "2.Goodbye!", "3.How are you?", "4.I am good, thank you!", "5.What is your name?",
             "6.My name is ___", "7.Where are you from?", "8.I am from ____.", "9.How old are you?",
             "10.I am ____ years old.", "11.Thank you!", "12.You are welcome!", "13.I don't know.", 
             "14.Can you speak slowly?", "15.Could you repeat that?", "16.I don't understand",
             "17.Excuse me.", "18.have a nice day!"];
var frnGen = ["1.Bonjour!", "2.Au revoir!", "3.Comment allez-vous", "4.Je vais bien, merci",
             "5.Comment vous appelez-vous?", "6.Je m'appelle", "7.D'où êtes-vous?",
             "8.Je suis de ___.", "9.Quel âge avez-vous?", "10.J'ai ___ ans",
              "11.Merci!", "12.De rien!", "13.Je ne sais pas.", "14.Peux-tu parler lentement?",
              "15.Pourriez-vous répéter?", "16.Je ne compreds pas.", "17.Excusez-moi.",
              "18.Bonne journée!"];
var spnGen = ["1.Hola!", "2.Adiós!", "3.Cómo estás?", "4.Estoy bien, gracias!", "5.Cuál es tu nombre?",
             "6.Mi nombre es ___.", "7.De dónde eres?", "8.Soy de ___.", "9.Cuántos años tienes?",
             "10.Tengo ___ años de edad.", "11.Gracias!", "12.Bienvenido.", "13.No lo sé.", 
             "14.Podrías hablar más lento.", "15.Podría repetir eso.", "16.No entiendo.",
             "17.Discúlpeme.", "18.Que tengas un buen día!"];
var gerGen = ["1.Hallo!", "2.Auf Wiedersehen!", "3.Wie geht es dir?", "4.Mir geht es gut, danke!", 
             "5.Wie heißt du?", "6.Ich heiße ___.", "7.Woher kommst du?", "8.Ich bin aus ___.",
             "9.Wie alt bist du?", "10.Ich bin ___ Jahre alt", "11.Danke!", "12.Bitteschön.",
             "13.Ich weiß nicht.", "14.Sprechen Sie Englisch?", "15.Können Sie langsamer sprechen?",
             "16.Ich verstehe nicht", "17.Entschuldigen Sie", "18.Einen schönen Tag noch!"];
var porGen = ["1.Olá!", "2.Tchau!", "3.Como você está?", "4.Estou bem, obrigado!", "5.Qual é o seu nome?",
             "6.Meu nome é ___.", "7.De onde você é?", "8.Eu sou de ___.", "9.Quantos anos você tem?", 
             "10.Eu tenho ___ anos de idade.", "11.Obrigado!", "12.Seja bem-vindo.", "13.Eu não sei.",
             "14.Você pode falar devagar?", "15.Você poderia repetir isso", "16.Eu não entendi.", 
             "17.Desculpe.", "18.Tenha um bom dia!"];
var gLan = [gerGen, engGen, spnGen, frnGen, porGen];
//Directions phrases
var engWay = ["1.Excuse me, where is ___?","2.Where can I find ___?","3.Where is the train station?",
              "4.Is it far?","5.Is it near ___?","6.Where is the washroom?","7.Where is the nearest ___?",
              "8.Where it is on the map?","9.Can you take me to ___?","10.Turn left","11.Turn right",
              "12.Go straight ahead","13.Go back","14.Go past the ___","15.Go toward the ___","16.Turn around",
              "17.At the end of the street","18.At the next stop","19.I am lost","20.The place is next to ___"];
var frnWay = ["1.Excusez-moi, où est  ___?","2.Où puis-je trouver ___?","3.Où est la gare?","4.Est-ce loin?",
              "5.Est-ce près de ___?","6.Où est la salle de bain?","7.Où il est sur la carte?",
              "8.Pouvez-vous me prendre à ___?","9.Je voudrais aller à ___","10.Tournez à gauche",
              "11.Tournez à droite","12.Allez tout droit","13.Retournez","14.Passez le ___",
              "15.Allez vers le ___","16.Faites demi-tour","17.Au bout de la rue","18.À l'arrêt suivant",
              "19.Je suis perdu","20.L'endroit est situé à côté ___"];
var spnWay =["1.Disculpe, ¿dónde está ___?","2.¿Dónde puedo encontrar___?","3.Donde esta la estacion de trenes",
             "4.¿Está lejos?","5.¿Está cerca de ___?","6.Donde esta el baño","7.¿Dónde está la más cercana",
             "8.Cuando está en el mapa","9.¿Puedes llevarme a","10.Gire a la izquierda.","11.Gire a la derecha.",
             "12.Siga recto.","13.Volver.","14.Ir más allá de la ___.","15.Ir hacia el ___.","16.Giro de vuelta.","17.Al final de la calle.",
             "18.En la siguiente parada.","19.Estoy perdido.","20.El lugar está al lado de ___"];           
var gerWay = ["1.Entschuldigung, wo ist ___?","2.Wo kann ich ___ finden?","3.Wo ist der Bahnhof?","4.Ist es weit?",
              "5.Ist es in der Nähe von ___?","6.Wo ist der Waschraum?","7.Wo ist der nächste ___?","8.Wo es auf der Karte?",
              "9.Können Sie mir nehmen, um ___","10.Biegen Sie links ab.","11.Biegen Sie rechts ab.","12.Fahren Sie geradeaus.",
              "13.Gehen Sie zurück.","14.Gehen Sie vorbei an der ___.","15.Gehen Sie in Richtung der ___.","16.Drehen Sie um.",
              "17.Am Ende der Straße","18.Beim nächsten Halt","19.Ich habe mich verirrt.","20.Der Ort ist neben"];
var porWay = ["1.Desculpe-me, onde é ___?","2.Onde posso achar___?","3.Onde é a estação de trem?","4.É longe?",
              "É perto de ___?","Onde é o banheiro","Onde está o mais próximo","Onde está no mapa","Você pode me levar para",
              "Vire à esquerda.","Vire à direita.","Vá em frente.","Volte.","Passe a ___.","Vá para a ___.",
              "Dê meia volta.","No fim da rua","Na próxima parada","Eu estou perdido.","O lugar é ao lado ___."];
var wLan = [gerWay, engWay, spnWay, frnWay, porWay];
//Friendly phrases
var engFri = ["1.Hello, what’s your name?","2.My name is ___.","3.Pleasure to meet you.","4.Do you mind if I sit here?","5.Is this chair taken?","6.Where do you live?",
              "7.I live in ___.","8.This is my friend ___.","9.I’m here on a business trip.","10.I’m on vacation.","11.I’m traveling with my family.",
              "12.Want to go eat?","13.Let’s go!","14.I had a wonderful time!","15.It was good talking to you.","16.Let’s stay in touch!",
              "17.What is your phone number?","18.Here is my email address.","19.Please come visit!","20.I hope to see you again soon!"];
var frnFri = ["1.Bonjour, comment vous appellez-vous?","2.Je m'appelle ___.","3.Ravi de vous rencontrer.","4.Ça vous dérange si je me mets assis ici?",
              "5.Est-ce que ce siège est pris?","6.Où habitez-vous?","7.Je vis en ___.","8.Voici mon ami ___.","9.Je suis ici en voyage d'affaires.",
              "10.Je suis en vacances.","11.Je voyage avec ma famille.","12.Voulez-vous aller manger?","13.Allons-y!","14.J'ai passé un moment fantastique!",
              "15.Il était bon de vous parler.","16.Restons en contact!","17.Quel est votre numéro de téléphone?","18.Voici mon adresse e-mail.",
              "19.Venez nous rendre visite!","20.J'espère te revoir bientôt!"];
var spnFri = ["1.Hola, ¿cómo te llamas?","2.Mi nombre es ___.","3.Un placer conocerlo.", "4.¿Te importa si me siento aquí?", "5.¿Está tomada esta silla?",
              "6.Dónde vives?","7.Yo vivo en ___.","8.Este es mi amigo ___.","9.Estoy aquí en un viaje de negocios.","10.Estoy de vacaciones.",
              "11.Estoy viajando con mi familia.","12.¿Quieres ir a comer?","13.Vamos!","14.Me lo pasé maravilloso!","15.Fue un placer hablar contigo.",
              "16.Vamos a estar en contacto!","17.Cuál es tu número de teléfono?","18.Aquí está mi dirección de correo electrónico.","19.Por favor, ven a visitarnos!",
              "20.Espero volver a verte pronto!"];
var gerFri = ["1.Hallo, wie heißt du?","2.Mein Name ist ___.","3.Freut mich.","4.Haben Sie etwas dagegen, wenn ich hier sitze?",
              "5.Ist dieser Stuhl frei?","6.Wo leben Sie?","7.Ich lebe in ___.","8.Das ist mein Freund ___.","9.Ich bin hier auf einer Geschäftsreise.",
              "10.Ich bin im Urlaub.","11.Ich reise mit meiner Familie.","12.Willst du essen gehen.","13.Lass uns gehen!","14.Ich habe mich sehr gut amüsiert!",
              "15.Es war gut, mit dir zu reden.","16.Lassen Sie uns in Kontakt bleiben!","17.Was ist Ihre Telefonnummer?","18.Hier ist meine E-Mail-Adresse.",
              "19.Bitte kommen Sie zu Besuch!","20.Ich hoffe, Sie bald wieder zu sehen!"];
var porFri = ["1.Olá, qual é o seu nome?","2.Meu nome é ___.","3.Prazer em conhecê-lo.","4.Você se importa se eu me sentar aqui?",
              "5.Essa cadeira está reservada?","6.Onde você mora?","7.Eu moro em ___.","8.Este é meu amigo ___.","9.Eu estou aqui em uma viagem de negócios.",
              "10.Eu estou de férias.","11.Estou viajando com a minha família.","12.Quer ir comer?","13.Vamos!","14.Eu tive um momento maravilhoso!",
              "15.Foi bom conversar com você.","16.Vamos manter contato!","17.Qual é o seu número de telefone?","18.Aqui está o meu endereço de e-mail.",
              "19.Por favor, venha visitar!","20.Eu espero vê-lo novamente em breve!"];
var fLan = [gerFri, engFri, spnFri, frnFri, porFri];
//Help phrases
var engHelp = ["1.I have an emergency!","2.Can you help me, please?","3.I need help!","4.Can I help you?",
              "5.Are you ok?","6.I lost my wallet.","7.I lost my passport.","8.We have been robbed!","9.Call the police!",
              "10.My address is ___.","11.There has been an accident.","12.My friend is hurt!","13.We need a doctor!",
              "14.Call an ambulance!","15.Can I use your phone?","16.Where is the closest hospital?","17.I am allergic to ___.",
              "18.Our car ran out of gas."];
var frnHelp = ["1.J'ai une urgence!","2.Pouvez-vous m'aider, s'il vous plaît?","3.J'ai besoin d'aide!","4.Puis-je vous aider?",
              "5.Est-ce que ça va?","6.J'ai perdu mon portefeuille.","7.J'ai perdu mon passeport.","8.Nous avons été volés!","9.Appelez la police!",
              "10.Mon adresse est ___.","11.Il y a eu un accident.","12.Mon ami est blessé!","13.Nous avons besoin d'un médecin!","14.Appelez une ambulance!",
              "15.Puis-je utiliser votre téléphone?","16.Où est l'hôpital le plus proche?","17.Je suis allergique à ___.","18.On est tombé en panne d'essence."];
var spnHelp = ["1.Tengo una emergencia!","2.¿Me puedes ayudar, por favor?","3.Necesito ayuda!","4.Puedo ayudarle?",
               "5.Estás bien?","6.Perdí mi cartera.","7.Perdí mi pasaporte.","8.Nos han robado!","9.Llame a la policía!",
               "10.Mi dirección es ___.","11.Hubo un accidente.","12.Mi amigo está herido!","13.Necesitamos un médico!",
               "14.Llame a la ambulancia!","15.Can yo uso el teléfono?","16.¿Dónde está el hospital más cercano?",
               "17.Soy alérgico a ___.","18.Nuestro coche se quedó sin gasolina."];
  var gerHelp = ["1.Es gibt einen Notfall!","2.Können Sie mir bitte helfen?","3.Ich brauche Hilfe!","4.Kann ich Ihnen helfen?",
               "5.Sind Sie in Ordnung?","6.Ich habe meinen Geldbeutel verloren.","7.Ich habe meinen Reisepass verloren.",
               "8.Wir wurden ausgeraubt!","9.Rufen Sie die Polizei!","10.Meine Adresse ist ___.","11.Es gab einen Unfall.",
               "12.Mein Freund ist verletzt!","13.Wir brauchen einen Arzt!","14.Rufen Sie einen Krankenwagen!","15.Darf ich Ihr Telefon verwenden?",
               "16.Wo ist das nächste Krankenhaus?","17.Ich bin allergisch gegen ___.","18.Wir haben kein Benzin mehr."];
var porHelp = ["1.Estou em uma situação de emergência!","2.Você pode me ajudar, por favor?","3.Eu preciso de ajuda!","4.Posso te ajudar?",
               "5.Você está bem?","6.Eu perdi a minha carteira.","7.Eu perdi o meu passaporte.","8.Nós fomos roubados!","9.Chame a polícia!",
               "10.Meu endereço é ___.","11.Houve um acidente.","12.Meu amigo está ferido!","13.Precisamos de um médico!","14.Chame uma ambulância!",
               "15.Posso usar seu telefone?","16.Onde está o hospital mais próximo?","17.Eu sou alérgico a ___.",
               "18.Nosso carro ficou sem gasolina"];
var hLan = [gerHelp, engHelp, spnHelp, frnHelp, porHelp];
//Shopping phrases
var engShp = ["1.When does the store open?","2.What time does the store close?", "3.What would you like?","4.I would like ___.", "5.I am looking for ___.",
             "6.Where can I find ___?", "7.I’m just looking around, thanks.","8.That will be all, thanks.","9.Where is the fitting room?", "10.Do you have this ___ in a bigger size?",
             "11.This ___ looks great on you!","12.How much does it cost?","13.Can I order this online?", "14.Do you have anything on sale?", "15.Can I have a receipt?",
             "16.Please sign here.", "17.Can I get a bag please?","18.Could you wrap this up for me?"];
var frnShp = ["1.A quelle heure le magasin ouvre-t-il?", "2.A quelle heure est la fermeture du magasin?", "3.Que désirez-vous?",
             "4.Je voudrais ___.", "5.Je cherche ___.", "6.Où puis-je trouver ___?", "7.Je suis juste en train de regarder, merci.",
             "8.Ce sera tout, merci.", "9.Où est la cabine d'essayage?","10.Avez-vous ce ___ dans une plus grande taille?","11.Ce ___ vous va très bien!",
             "12.Combien ça coûte?","13.Puis-je commander en ligne?","14.Avez-vous quelque chose en soldes?","15.Puis-je avoir un reçu?",
             "16.Signez ici, s'il vous plaît","17.Puis-je obtenir un sac s'il vous plaît?","18.Pourriez-vous l'emballer?"];
var gerShp = ["1.Wann ist der Laden offen?", "2.Wann schließt der Laden?", "3.Was haetten Sie gerne?",
             "4.Ich möchte ___.", "5.Ich suche ___.", "6.Wo finde ich ___?", "7.Ich schaue mich nur mal um , danke.",
             "8.Das wird alles sein, danke.", "9.Wo ist der Umkleidekabine?","10.Haben Sie in einem größeren Format haben diese ___?","11.Dieses ___ schaut auf Sie!",
             "12.Wie viel kostet es?","13.Kann ich diese online zu bestellen?","14.Haben Sie alles bieten Angebote an?","15.Kann ich bitte eine Quittung haben?",
             "16.Unterschreiben Sie bitte hier.","17.Kann ich bitte eine Tasche haben?","18.Könnten Sie das für mich einpacken?"];
var spnShp = ["1.¿Cuándo se abre la tienda?", "2.¿A qué hora cierran la tienda?", "3.Qué le gustaría?",
             "3.Me gustaría ___.", "4.Busco a ___.", "5.¿Dónde puedo encontrar ___?", "6.Sólo estoy mirando a su alrededor, gracias.",
             "7.Eso es todo, gracias.", "8.¿Dónde está el probador?","9.¿Tiene este ___ en un tamaño más grande?","10.Esto ___ se ve muy bien en ti!",
             "11.Cuánto cuesta?","12.¿Puedo ordenar esto en línea?","13.¿Tiene algo en oferta?","14.¿Puedo tener un recibo por favor?",
             "15.Por favor firme aquí.","16.¿Puede darme una bolsa por favor?","17.¿Podrías envolverlo por favor?","18.¿Cuál es tu política de devolución?"];
var porShp = ["1.Quando é que a loja abre?", "2.A que horas a loja fecha?", "3.O que você gostaria?",
             "4.Eu gostaria de ___.", "5.Estou à procura de ___.", "6.Onde posso encontrar ___?", "7.Eu só estou dando uma olhada, obrigado.",
             "8.Isso é tudo, obrigado.", "9.Onde fica o provador?","10.Você tem esse ___ em um tamanho maior?","11.Este ___ fica bem em você!",
             "12.Quanto custa isso?","13.Posso fazer esse pedido online?","14.Você tem alguma coisa em promoção?","15.Por favor, posso ter um recibo?",
             "16.Assine aqui, por favor.","17.Posso pegar uma sacola, por favor?","18.Você poderia embrulhar isso para mim?"];
var sLan = [gerShp, engShp, spnShp, frnShp, porShp];
var superLan = [gLan, fLan, wLan, sLan, hLan];
//Main title card
var main = new UI.Card({
 style: 'large',
 title: 'Plingo',
 body: 'Up to set\nnative lang\nDown for translations' 
});
main.show();
//Language selection
main.on('click', 'up', function(e) {
  var nlmenu = new UI.Menu({ 
    sections: [{
      title: 'Pick Native Language', 
      items: [{      
        title: 'Deutsche',
        }, {
        title: 'English',
        }, {
        title: 'Español',       
        }, {
        title: 'Français',
        }, {
        title: 'Português',
      }]
    }]
  });
  
  //What happens when a language is picked
  nlmenu.on('select', function(e) {
    natlan = e.itemIndex;
  });
  nlmenu.show();
});
//A bit about Plingo, and its creators
main.on('click', 'select', function(e) {
  var wind = new UI.Window({
    fullscreen: true,
  });
  var textfield = new UI.Text({
    position: new Vector2(0, 65),
    size: new Vector2(144, 30),
    font: 'gothic-24-bold',
    text: 'Welcome to Plingo!',
    subtext: 'Made by Hamid, Peter, and Natasha', 
    textAlign: 'center'
  });
  wind.add(textfield);
  wind.show();
});
//Finding translation
main.on('click', 'down', function(e) {
  if (natlan === ''){
    var wind = new UI.Window({
      fullscreen: true,
    });
    //If no native language has been picked yet
    var textField = new UI.Text({
      position: new Vector2(0, 65),
      size: new Vector2(144, 30),
      font: 'gothic-24-bold',
      text: 'Pick a native language first!',
      textAlign: 'center',
    });
    wind.add(textField);
    wind.show();
  }
  else if (natlan >= 0){
  var tlmenu = new UI.Menu({ 
    sections: [{
      title: pickLan[natlan],//Pick translation language
      items: [{      
        title: lLan[natlan][0],
        }, {
        title: lLan[natlan][1],
        }, {
        title: lLan[natlan][2],       
        }, {
        title: lLan[natlan][3],       
        }, {
        title: lLan[natlan][4],
      }]
    }]
  });
  
  //What happens when a language is picked
  tlmenu.on('select', function(e) {
    translan = e.itemIndex;
    direc();
  });
  tlmenu.show();
  }
});
//Category of terms, such as shopping, directions, etc
function direc(){
  var clmenu = new UI.Menu({ 
    sections: [{
      title: direcLan[natlan],//Change to language definition
      items: [{      
        title: dLan[natlan][0],
        }, {
        title: dLan[natlan][1],
        }, {
        title: dLan[natlan][2],       
        }, {
        title: dLan[natlan][3],       
        }, {
        title: dLan[natlan][4],
      }]
    }]
  });
  
  //Accessing the terms and phrases of each directory for each directory
  clmenu.on('select', function(e) {
    dirlan = e.itemIndex;
    allPhrases();
  });
 clmenu.show();
}
function allPhrases(){
  var plmenu = new UI.Menu({ 
    sections: [{
      title: phraLan[natlan],//Phrases and questions 
      items: [{
        title: superLan[dirlan][natlan][0],
        subtitle: superLan[dirlan][translan][0],
        font: 'gothic-14'
        }, {
        title: superLan[dirlan][natlan][1],
        subtitle: superLan[dirlan][translan][1],
        }, {
        title: superLan[dirlan][natlan][2],
        subtitle: superLan[dirlan][translan][2],
        }, {
        title: superLan[dirlan][natlan][3], 
        subtitle: superLan[dirlan][translan][3],
        }, {
        title: superLan[dirlan][natlan][4], 
        subtitle: superLan[dirlan][translan][4],
        }, {
        title: supe
