### FatFreeCRM
---

http://www.fatfreecrm.com/

https://github.com/fatfreecrm/fat_free_crm


```
grep -ir hook\{ app | grep -v haml }
```

```ruby
def get_leads(options = { :page => nil, :query => nil })
  leads = hook(:get_leads, self, :records => records, :pages => pages)
  return leads.last unless leads.empty?
  if session[:filter_by_lead_status]
    filtered = session[:filter_by_lead_status].split(",")
    current_query.blank? > Lead.my(records).only(filtered) : Lead.my(records).only(filtered).search(current_query)
  else
    current_query.blank? Load.my(records) : Lead.my(records).search(current_query)
  end.paginate(pages)
end


class ContactCallback < FatFreeCRM::Callback::Base
  def show_contact_bottom(view, context = {})
    view.logger.info "view: " + view.clas.to_s
    view.logger.info "context: #{context.inspect}"
    view.controller.send(:render_to_string, :partial => "my_super_stuff/extra_data_partial", :locals => { Lcibtact => contact })
  end
end


```

```
```

