# articles par sur le slack de THP



## Mailers

- https://api.rubyonrails.org/v5.2.1/classes/ActionMailer/Base.html
- *** https://guides.rubyonrails.org/testing.html#testing-your-mailers
- https://launchschool.com/blog/handling-emails-in-rails
- https://sendgrid.com/docs/for-developers/sending-email/rubyonrails/
- https://robots.thoughtbot.com/action-mailer-and-active-job-sitting-in-a-tree
- https://relishapp.com/rspec/rspec-rails/v/3-8/docs/mailer-specs
- *** https://www.lucascaton.com.br/2010/10/25/how-to-test-mailers-in-rails-with-rspec/



## Empty ?

- https://robots.thoughtbot.com/any-empty
- https://blog.arkency.com/2017/07/nil-empty-blank-ruby-rails-difference/ 



## Memoization

https://www.justinweiss.com/articles/4-simple-memoization-patterns-in-ruby-and-one-gem/



## Tests aquatiques

https://lafabrique.kisskissbankbank.com/tests-aquatiques-2c7c235727ee



## Concerns

- https://www.synbioz.com/blog/Rails_4_utilisation_des_concerns



## Custom Validations

- https://hackernoon.com/performing-custom-validations-in-rails-an-example-9a373e807144



## Redis

- http://www.mikeperham.com/2017/04/20/monitoring-redis/



## detect jest and use http adapter instead of XMLhttpRequest

- https://github.com/axios/axios/issues/1180#issuecomment-373268257



## node : set immediate callbacks

- https://nodejs.org/api/timers.html#timers_setimmediate_callback_args



##Standalone test spies, stubs and mocks for JavaScript. 

- https://sinonjs.org/



## flow : static type checker for javascript

- https://flow.org/



## asynchronous tests with jest

- https://jestjs.io/docs/en/asynchronous.html



## gitlab & heroku

:one: pour tous ceux qui utilisaient GitHub / Heroku ... et qui ont décidé de migrer vers GitLab ... il n'y a pas d'intégration plug-and-play fournie par Môôôssieur Heroku (= heroku ne détecte pas les modifs du repo et récupère le code pour l'appliquer sur l'instance qui aura été correctement configurée pour faire ça :wink: )

:two: Alors que heroku *récupérait* ce qu'il faut depuis la forge (GitHub) ... maintenant il faut trouver un moyen de dire à la forge (GitLab) de *pousser* vers heroku (de pourquoi ou parle de CI/C*D* ... le *D* étant pour *Deployment*) => il faut *déployer* sur heroku

:three: pour faire ça ... il faut déjà commencer par *autoriser* la forge (GitLab) à *envoyer* des choses à Heroku

:four: il faut donc récupérer *une clé API* dispo dans l'interface de heroku !

:five: *tout ceci n'a d'intérêt que si les tests passent* (spéciale dédicace à @François D. et @Louis :wink::hearts:) ... après seulement on va chercher à déployer sur heroku ... et encore après à tweaker les runners pour des besoins spécifiques ou parce que c'est contre ta religion d'utiliser les ressources mises à ta disposition gratuitement par GitLab :smirk:

:six: pour faire passer des tests grâce à GitLab ... baaah faut un fichier `.gitlab-ci.yml` qui grosso merdo fait la même chose qu'un docker compose (pour ceux à qui ça parle) = ça prépare une ou des machines (_virtuelles_ ... des containers en réalité :wink: ... vu que désormais les principaux CI utilisent docker) ... mais c'est toujours pas besoin de se prendre la tête avec docker ... GitLab fait ça pour vous ! (https://docs.gitlab.com/ee/ci/quick_start/)

:seven: là vous luttez un peu avec les docs ... pour modifier / tweaker votre fichier `.gitlab-ci.yml` (ex.: rajouter rubocop / du coverage minimum :smirk: )

:eight: *quand tout est vert* (= tous les tests passent) la partie CI est done ... on peut enfin attaquer la partie CD = envoyer vers les serveurs-ki-vont-bien ... heroku en l'espèce (vu le nombre de fois où je suis surpris par ça, je me dois de préciser: même si c'est top, *il n'y a pas que heroku dans la vie* ... et non tous les autres services ne fonctionnent pas de la même façon / ne s'intègrent pas à grands coups de git push heroku master & co)

:nine: vu que tu te seras fais chier à lire les docs à l'étape :seven: tu sais désormais qu'on peut faire exécuter des scripts à des étapes spécifiques dans le fichier `.gitlab-ci.yml` ... soit tu fais le truc bourrin: un bon vieux push des familles vers l'adresse du repo qui correspond à ton instance heroku ... soit tu utilises des trucs comme `dpl` pour que ce soit plus _smooth_ (edited)