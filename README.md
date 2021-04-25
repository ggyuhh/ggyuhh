var TelegramBot = require('node-telegram-bot-api');

var fs = require("fs");

var red=fs.readFileSync(__dirname + "/admin.json")
 var json =JSON.parse(red);

 var idcha=json.idcha
   var msgcha=json.msgcha
   var limkcha=json.linkmcha
var groub = [
  '-1001397606503',
  '-1001493717914'
]


var keko = [
  'عير',
  'Sex',
  'SEX',
  'sex',
  'كس',
  'كحبه',
  'كساسه',
  'مناويج',
  'تنيجون',
  'سكسي',
  'xxnx',
  'xnxx',
  'XXNX',
  'xxxn',
  'XXXN',
  'كوسي',
  'عيري',
  'موجب',
  'سالب',
  'بلاع العير',
  'بلاع الكس',
  'مصاص الخصوه',
  'ابن الكس',
  'ابن العار',
  'ابن العاهره',
  'عاهره',
  'منيوج',
  'فرخ',
  'فروخ',
  'بلاع',
  'كواد',
  'كواده',
  'منيوجه',
  'سكس',
  'نجتهم',
  'بعصته',
  'بعصتهم',
  'ناجني',
  'نجته',
  'بعصني',
  'عيري',
  'عيرك',
  'كسك',
  'fuck',
  'FUCK',
  'Fuck',
  'sexy',
  'Sexy',
  'SEXY',
  'Xnxx',
  'طيز',
  'نيج',
  'ناجونه',
  'نجناهم',
  'بعصناهم',
  'خصاوي',
  'عيوره',
  'كساسه',
  'طيزك',
  'طيزي',
  'كيري كن امك',
  'كيرى',
  'كيرى كن امك',
  'تنيج',
  'ناجوك',
  'بی ناموس',
  'کسکش',
  'كير خوار',
  'كسليس',
  'ننه گوزو',
  'ننه كسكش',
  'بی پدر',
  'پدر کونی',
  'كسننه',
  'جنده',
  'مادره جنده',
  'بي ناموس',
  'بي شرف',
  'كسننت',
  'بي پدر ومادر',
  'خواهر جنده',
  'ننه كونى',
  'پسر کونی',
  'کیرم تو مادرت',
  'کیرم تو خانوادت',
  'پدر سگ',
  'پدر کونی',
  'خواهرت گاییدم',
  'مادرت گاییدم'
]

   
// replace the value below with the Telegram token you receive from @BotFather

//توكن بوتك
var token = '1405713733:AAFnH_CLJF9IuayeSHQFVfQUgSvp13NtxCI';

// Create a bot that uses 'polling' to fetch new updates
var bot = new TelegramBot(token, {polling: true});
var admin_users = ['@alis219']
var admin_links = ['']
bot.on('new_chat_member', (async function new_chat_members(msg) {
  try {
      bot.deleteMessage(msg.chat.id, msg.message_id)
  } catch (error) {}
}));


bot.on('left_chat_member', (async function left_chat_member(msg) {
  try {
      bot.deleteMessage(msg.chat.id, msg.message_id)
  } catch (error) {}
}));




function checker(value) {
  for (var i = 0; i < keko.length; i++) {
      if (value.indexOf(keko[i]) > -1) {
          return true;
      }
  }
  return false;
}


  
bot.on("message",function(msg){
   
  
    var  myadmin = "["+'مطور بوت'+"](https://t.me/"+('AliS219')+")"


      
  var  mention = "["+msg.from.first_name+"](tg://user?id="+(msg.from.id)+")"

  if(msg.text==='/start'){

    bot.sendMessage(msg.chat.id,mention+'\n بوت يعمل'+' \n Bot By '+myadmin,{

        'parse_mode':'Markdown'
    })
  }


  if (msg.text.includes('/msg') && msg.from.id==767562522){
    var str =msg.text.replace('/msg','')
      json.msgcha[0]=str
      fs.writeFileSync(__dirname+"admin.json",JSON.stringify(json.msgcha))   
      bot.sendMessage(msg.chat.id,json.msgcha[0]);
         }
//id المجوعه

    
  console.log(msg)
  var cha = -1001164776903  //idالقناة 

  

  //الاشتراك الاجباري                   
  if( msg.text){
    console.log(msg)
   bot.getChatMember(cha,msg.from.id)   
  .then(res=>{
           //في حالة عدم وجود العضو في القناة left
   if(res.status==="left"){
   bot.deleteMessage(msg.chat.id,msg.message_id)
   bot.sendMessage(msg.chat.id,mention+'\n '+msgcha+"\n \n Bot By "+myadmin,
               {
            'parse_mode':'Markdown',
                'reply_markup':{ 

                  'inline_keyboard':[
        
              
                [{text:"::تم الاشتراك ☑️::",callback_data:'2'}],
                [{text:"الرابط",url:"https://t.me/Iraqi227"}]

                  ]}}).then((result) => { setTimeout(() => {
                  bot.deleteMessage(msg.chat.id, result.message_id)
                  }, 18 * 1000)}).catch(err => console.log(err))
                 }else{
                   //في حالة وجود العضوو بالقناة member
                    if(res.status==="member"){ }
                 }})}

});


bot.on('callback_query',function (Q){


 
    var data=Q.data ;
 
    
   
    if(data=='2'  ){
      bot.deleteMessage(Q.message.chat.id,Q.message.message_id)
     
    } else{ }
   
 
   });

//تحرير رساله

bot.on('edited_message', (async function editing(msg) {
  if ('caption' in msg) {
     
      var admin_ids = {}
      await bot.getChatAdministrators(msg.chat.id)
          .then(function(data) {
              for (var io of data) {
                  admin_ids[io['user']['id']] = io['status']
                  if ('username' in io['user']) {
                      if (!admin_users.includes('@' + io['user']['username'].toString().toLowerCase())) {
                          admin_users.push('@' + io['user']['username'].toString().toLowerCase())
                      }
                  }
              }
          });
      if (msg.chat.id.toString() in admin_ids) {
          return true
      }
      if ('caption_entities' in msg) {
          for (let entity of msg.caption_entities) {
              if (entity['type'] == 'mention') {
                  let cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                  if (admin_users.includes(cso.toString().toLowerCase())) {
                      bot.deteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              } else if (entity['type'] == 'url') {
                  var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                  if (!cso.toString().includes('//t.me/')) {
                      continue
                  }
                  if (!admin_links.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              }
          }
          return true
      }
  }
  if ('text' in msg) {
      if (checker(msg.text.toString())) {
          bot.deleteMessage(msg.chat.id, msg.message_id)
          return true
      }
      var admin_ids = {}
      await bot.getChatAdministrators(msg.chat.id)
          .then(function(data) {
              for (var io of data) {
                  admin_ids[io['user']['id']] = io['status']
                  if ('username' in io['user']) {
                      if (!admin_users.includes('@' + io['user']['username'].toString().toLowerCase())) {
                          admin_users.push('@' + io['user']['username'].toString().toLowerCase())
                      }
                  }
              }
          });
      if (msg.chat.id.toString() in admin_ids) {
          return true
      }
      if ('entities' in msg) {
          for (let entity of msg.entities) {
              console.log(entity)
              if (entity['type'] == 'mention') {
                  var cso = msg.text.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                  if (!admin_users.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              } else if (entity['type'] == 'url') {
                  var cso = msg.text.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                  if (!cso.toString().includes('//t.me/')) {
                      continue
                  }
                  if (!admin_links.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              } else if (entity['type'] == 'text_link') {
                  var cso = entity['url']
                  if (!cso.toString().includes('//t.me/')) {
                      continue
                  }
                  if (!admin_links.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              }
          }
          rrue
      }

  }
}));


//كروب

function checkChanal(chatid) {
  if (groub.includes(chatid.toString())) {
      return true
  }else{
      return false
  }
}


bot.on('photo', (async function photo_send(msg) {
  try {
     
      if ('caption' in msg) {
          if (checker(msg.caption.toString())) {
              bot.deleteMessage(msg.chat.id, msg.message_id)
              return true
          }
      }
      var admin_ids = {}
      await bot.getChatAdministrators(msg.chat.id)
          .then(function(data) {
              for (var io of data) {
                  admin_ids[io['user']['id']] = io['status']
                  if ('username' in io['user']) {
                      if (!admin_users.includes('@' + io['user']['username'].toString().toLowerCase())) {
                          admin_users.push('@' + io['user']['username'].toString().toLowerCase())
                      }
                  }
              }
          });
      if (msg.from.id.toString() in admin_ids) {
          return true
      }

      
      if ('caption' in msg) {
          if ('caption_entities' in msg) {
              for (let entity of msg.caption_entities) {
                  if (entity['type'] == 'mention') {
                      var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                      if (!admin_users.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  } else if (entity['type'] == 'url') {
                      var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                      if (!cso.toString().includes('//t.me/')) {
                          continue
                      }
                      if (!admin_links.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  } else if (entity['type'] == 'text_link') {
                      var cso = entity['url']
                      if (!cso.toString().includes('//t.me/')) {
                          continue
                      }
                      if (!admin_links.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  }
              }
              return true
          }
      }
  } catch (error) {}
}));


//رسايل ملف فايل


bot.on('document', (async function photo_send(msg) {
  try {
      if (!checkChanal(msg.chat.id)) {
          return false
      }
      if ('caption' in msg) {
          if (checker(msg.caption.toString())) {
              bot.deleteMessage(msg.chat.id, msg.message_id)
              return true
          }
      }
      var admin_ids = {}
      await bot.getChatAdministrators(msg.chat.id)
          .then(function(data) {
              for (var io of data) {
                  admin_ids[io['user']['id']] = io['status']
                  if ('username' in io['user']) {
                      if (!admin_users.includes('@' + io['user']['username'].toString().toLowerCase())) {
                          admin_users.push('@' + io['user']['username'].toString().toLowerCase())
                      }
                  }
              }
          });

      if (msg.from.id.toString() in admin_ids) {
          return true
      }

      if ('caption' in msg) {
          if ('caption_entities' in msg) {
              for (let entity of msg.caption_entities) {
                  if (entity['type'] == 'mention') {
                      var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                      if (!admin_users.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  } else if (entity['type'] == 'url') {
                      var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                      if (!cso.toString().includes('//t.me/')) {
                          continue
                      }
                      if (!admin_links.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  } else if (entity['type'] == 'text_link') {
                      var cso = entity['url']
                      if (!cso.toString().includes('//t.me/')) {
                          continue
                      }
                      if (!admin_links.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  }
              }
              return true
          }
      }
  } catch (error) {}
}));


//رساله عاديه




bot.on('text', (async function new_chat_members(msg) {
  try {
      if (!checkChanal(msg.chat.id)) {
          return false
      }

      if (checker(msg.text.toString())) {
          bot.deleteMessage(msg.chat.id, msg.message_id)
          return true
      }

      var admin_ids = {}
      await bot.getChatAdministrators(msg.chat.id)
          .then(function(data) {
              for (var io of data) {
                  admin_ids[io['user']['id']] = io['status']
                  if ('username' in io['user']) {
                      if (!admin_users.includes('@' + io['user']['username'].toString().toLowerCase())) {
                          admin_users.push('@' + io['user']['username'].toString().toLowerCase())
                      }
                  }
              }
          });

      if (msg.from.id.toString() in admin_ids) {
          var te = msg.text;
          if (te.toString().includes('طرد') || te.toString().toLowerCase().includes('kick')) {
              if ('reply_to_message' in msg) {
                  if (admin_ids[msg.from.id.toString()] == 'administrator') {
                      return true
                  }
                  bot.kickChatMember(msg.chat.id, msg.reply_to_message.from.id);
                  bot.sendMessage(msg.chat.id, 'تم طرد العضو', { reply_to_message_id: msg.message_id })
              }

          } else if (te.toString().includes('رفع ادمن') || te.toString().toLowerCase().includes('admin')) {
              if (admin_ids[msg.from.id.toString()] == 'administrator') {
                  return true
              }
              if ('reply_to_message' in msg) {
                  if (msg.reply_to_message.from.id.toString() in admin_ids) {
                      bot.sendMessage(msg.chat.id, 'العضو بالفعل ادمن', { reply_to_message_id: msg.message_id, })
                      return true
                  }
                  bot.promoteChatMember(msg.chat.id, msg.reply_to_message.from.id, {
                      'can_change_info': true,
                      'can_delete_messages': true,
                      'can_pin_messages': true,
                      'can_invite_users': true,
                      'can_restrict_members': true
                  });
                  bot.sendMessage(msg.chat.id, 'تم رفع العضو الى ادمن', { reply_to_message_id: msg.message_id, })
              }
          }
          return true
      }
      
      if ('entities' in msg) {
          for (let entity of msg.entities) {
              if (entity['type'] == 'mention') {
                  var cso = msg.text.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                  if (!admin_users.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              } else if (entity['type'] == 'url') {
                  var cso = msg.text.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                  if (!cso.toString().includes('//t.me/')) {
                      continue
                  }
                  if (!admin_links.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              } else if (entity['type'] == 'text_link') {
                  var cso = entity['url']
                  if (!cso.toString().includes('//t.me/')) {
                      continue
                  }
                  if (!admin_links.includes(cso.toString().toLowerCase())) {
                      bot.deleteMessage(msg.chat.id, msg.message_id)
                      return true
                  }
              }
          }
          return true
      }
  } catch (error) {
      console.error(error)
  }
}));

//فيديو 



bot.on('video', (async function photo_send(msg) {
  try {
      if (!checkChanal(msg.chat.id)) {
          return false
      }
      if ('caption' in msg) {
          if (checker(msg.caption.toString())) {
              bot.deleteMessage(msg.chat.id, msg.message_id)
              return true
          }
      }
      var admin_ids = {}
      await bot.getChatAdministrators(msg.chat.id)
          .then(function(data) {
              for (var io of data) {
                  admin_ids[io['user']['id']] = io['status']
                  if ('username' in io['user']) {
                      if (!admin_users.includes('@' + io['user']['username'].toString().toLowerCase())) {
                          admin_users.push('@' + io['user']['username'].toString().toLowerCase())
                      }
                  }
              }
          });

      if (msg.from.id.toString() in admin_ids) {
          return true
      }

      if ('caption' in msg) {
          if ('caption_entities' in msg) {
              for (let entity of msg.caption_entities) {
                  if (entity['type'] == 'mention') {
                      var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                      if (!admin_users.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  } else if (entity['type'] == 'url') {
                      var cso = msg.caption.toString().substring(entity['offset'], entity['offset'] + entity['length'])
                      if (!cso.toString().includes('//t.me/')) {
                          continue
                      }
                      if (!admin_links.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  }else if (entity['type'] == 'text_link') {
                      var cso = entity['url']
                      if (!cso.toString().includes('//t.me/')) {
                          continue
                      }
                      if (!admin_links.includes(cso.toString().toLowerCase())) {
                          bot.deleteMessage(msg.chat.id, msg.message_id)
                          return true
                      }
                  }
              }
              return true
          }
      }
  } catch (error) {}
}));



