package cn.keith.aifenxiang.fragment;

import cn.keith.aifenxiang.R;
import cn.keith.aifenxiang.activity.HomeActivity;
import android.os.Bundle;
import android.support.v4.app.Fragment;
import android.support.v4.app.FragmentActivity;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.AdapterView;
import android.widget.AdapterView.OnItemClickListener;
import android.widget.AdapterView.OnItemSelectedListener;
import android.widget.ArrayAdapter;
import android.widget.ListView;

public class SilidingMenuFragmen extends Fragment {

	private ArrayAdapter adapter;

	private String[] arr = { "菜单一", "菜单二", "菜单三" };

	private ListView listView;

	@Override
	public View onCreateView(LayoutInflater inflater, ViewGroup container,
			Bundle savedInstanceState) {

		listView = new ListView(getActivity());

		adapter = new ArrayAdapter<String>(getActivity(),
				android.R.layout.simple_list_item_1, arr);

		listView.setAdapter(adapter);

		return listView;
	}

	@Override
	public void onActivityCreated(Bundle savedInstanceState) {
		// TODO Auto-generated method stub
		super.onActivityCreated(savedInstanceState);

		listView.setOnItemClickListener(new OnItemClickListener() {

			@Override
			public void onItemClick(AdapterView<?> parent, View view,
					int position, long id) {
				HomeActivity activity = (HomeActivity) getActivity();
				switch (position) {
				case 0:
					Menu_1_Fragment menu_1_Fragment = new Menu_1_Fragment();

					activity.replace(R.id.homefragment_fg, menu_1_Fragment,
							"menu_1_Fragment");
					break;
				case 1:
					activity.replace(R.id.main_fl, new Menu_2_Fragment(),"menu_2_Fragment");

					Menu_2_Fragment menu_2_Fragment = new Menu_2_Fragment();

					activity.replace(R.id.homefragment_fg, menu_2_Fragment,
							"menu_2_Fragment");
					break;
				case 2:
					activity.replace(R.id.homefragment_fg, new Menu_2_Fragment(),"menu_3_Fragment");

					Menu_3_Fragment menu_3_Fragment = new Menu_3_Fragment();

					activity.replace(R.id.main_fl, menu_3_Fragment,
							"menu_2_Fragment");
					break;

				default:
					break;
				}
			}

		});
	}

}
